# Portafolio-Ubaldo
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portafolio de Uvaldo</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background: linear-gradient(135deg, #1a2a6c, #3a7bd5);
            color: white;
            text-align: center;
            padding: 2.5rem 0;
            margin-bottom: 2rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .nombre {
            font-size: 1.3rem;
            font-weight: normal;
            opacity: 0.9;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        .materia {
            background-color: white;
            border-radius: 12px;
            padding: 2.5rem;
            margin-bottom: 3rem;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .materia:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
        }
        
        .fisica {
            border-left: 5px solid #ff7e5f;
        }
        
        .sm2 {
            border-left: 5px solid #4CA1AF;
        }
        
        h2 {
            color: #2c3e50;
            border-bottom: 3px solid;
            padding-bottom: 0.7rem;
            margin-bottom: 2rem;
            font-size: 2rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
        }
        
        .fisica h2 {
            border-color: #ff7e5f;
        }
        
        .sm2 h2 {
            border-color: #4CA1AF;
        }
        
        h2 i {
            margin-right: 10px;
            font-size: 1.8rem;
        }
        
        .galeria {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
        }
        
        .imagen-container {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            background: white;
            height: 250px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
        
        .imagen-container:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
        }
        
        .imagen-container.vacio {
            border: 2px dashed #ccc;
            background-color: #f9f9f9;
        }
        
        .imagen-container.vacio:hover {
            border-color: #4CA1AF;
            background-color: #f0f7ff;
        }
        
        .imagen-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }
        
        .icono-agregar {
            font-size: 3rem;
            color: #ccc;
        }
        
        .imagen-container.vacio:hover .icono-agregar {
            color: #4CA1AF;
        }
        
        .texto-agregar {
            margin-top: 10px;
            color: #777;
            font-size: 0.9rem;
            text-align: center;
        }
        
        .pie-imagen {
            padding: 15px;
            background-color: #f8f9fa;
            text-align: center;
            font-size: 0.95rem;
            color: #555;
            border-top: 1px solid #eee;
        }
        
        .instrucciones {
            background: #e3f2fd;
            border-left: 4px solid #2196F3;
            padding: 15px;
            margin: 20px 0;
            border-radius: 4px;
            font-size: 0.9rem;
        }
        
        footer {
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
            background: linear-gradient(135deg, #2C3E50, #1a2a6c);
            color: white;
        }
        
        .contador {
            background: #f8f9fa;
            padding: 10px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            color: #666;
        }
        
        /* Visor de imágenes */
        .visor {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .visor-contenido {
            max-width: 90%;
            max-height: 90%;
            position: relative;
        }
        
        .visor img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            border-radius: 8px;
        }
        
        .cerrar {
            position: absolute;
            top: 15px;
            right: 35px;
            color: #fff;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            z-index: 1001;
        }
        
        .cerrar:hover {
            color: #bbb;
        }
        
        .anterior, .siguiente {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            color: white;
            font-size: 30px;
            font-weight: bold;
            padding: 16px;
            cursor: pointer;
            user-select: none;
            transition: 0.3s;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 50%;
            z-index: 1001;
        }
        
        .anterior:hover, .siguiente:hover {
            background-color: rgba(0, 0, 0, 0.8);
        }
        
        .anterior {
            left: 20px;
        }
        
        .siguiente {
            right: 20px;
        }
        
        .boton-eliminar {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(255, 0, 0, 0.7);
            color: white;
            border: none;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            cursor: pointer;
            display: none;
            z-index: 10;
            transition: background 0.3s;
        }
        
        .boton-eliminar:hover {
            background: rgba(255, 0, 0, 0.9);
        }
        
        .imagen-container:hover .boton-eliminar {
            display: block;
        }

        .estado-guardado {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #4CAF50;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            display: none;
            z-index: 1001;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        
        .boton-limpiar {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9rem;
            margin-top: 10px;
            transition: background 0.3s;
        }
        
        .boton-limpiar:hover {
            background: #ff5252;
        }
        
        @media (max-width: 768px) {
            .galeria {
                grid-template-columns: repeat(auto-fill, minmax(100%, 1fr));
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            h2 {
                font-size: 1.7rem;
                flex-direction: column;
                align-items: flex-start;
            }
            
            .contador {
                margin-top: 10px;
                margin-left: 0;
            }
            
            .materia {
                padding: 1.5rem;
            }
            
            .anterior, .siguiente {
                font-size: 24px;
                padding: 12px;
            }
        }
    </style>
</head>
<body>
    <!-- Estado de guardado -->
    <div id="estadoGuardado" class="estado-guardado">
        <i class="fas fa-check"></i> Imágenes cargadas
    </div>

    <!-- Visor de imágenes -->
    <div id="visor" class="visor">
        <span class="cerrar" id="cerrarVisor">&times;</span>
        <span class="anterior" id="anteriorImg">&#10094;</span>
        <span class="siguiente" id="siguienteImg">&#10095;</span>
        <div class="visor-contenido">
            <img id="imagenVisor" src="" alt="Imagen ampliada">
        </div>
    </div>

    <header>
        <div class="container">
            <h1>Portafolio de Uvaldo</h1>
            <p class="nombre">Rivas Pérez Marco Alejandro</p>
        </div>
    </header>
    
    <div class="container">
        <section class="materia fisica">
            <h2>
                <span><i class="fas fa-atom"></i> Física</span>
                <span class="contador" id="contadorFisica">0/15 imágenes</span>
            </h2>
            
            <div class="instrucciones">
                <p><strong>Instrucciones:</strong> Las imágenes se cargan automáticamente desde la carpeta del proyecto con nombres IMG_1ENERGIA.jpg a IMG_15ENERGIA.jpg.</p>
                <p><i class="fas fa-info-circle"></i> Si una imagen no existe, se mostrará un cuadro vacío.</p>
            </div>
            
            <div class="galeria" id="galeria-fisica">
                <!-- Los contenedores se generarán con JavaScript -->
            </div>
        </section>
        
        <section class="materia sm2">
            <h2>
                <span><i class="fas fa-code"></i> SM2 - Programación</span>
                <span class="contador" id="contadorSm2">0/9 imágenes</span>
            </h2>
            
            <div class="instrucciones">
                <p><strong>Instrucciones:</strong> Las imágenes se cargan automáticamente desde la carpeta del proyecto con nombres IMG_1SM2.jpg a IMG_9SM2.jpg.</p>
                <p><i class="fas fa-info-circle"></i> Si una imagen no existe, se mostrará un cuadro vacío.</p>
            </div>
            
            <div class="galeria" id="galeria-sm2">
                <!-- Los contenedores se generarán con JavaScript -->
            </div>
        </section>
    </div>
    
    <footer>
        <div class="container">
            <p>Portafolio de Materias - Rivas Pérez Marco Alejandro</p>
            <p>Física (<span id="contadorFooterFisica">0</span>/15 imágenes) | SM2 (<span id="contadorFooterSm2">0</span>/9 imágenes)</p>
            <p style="margin-top: 10px; font-size: 0.9rem; opacity: 0.8;">
                <i class="fas fa-sync-alt"></i> Las imágenes se cargan automáticamente al abrir la página
            </p>
            <button class="boton-limpiar" onclick="recargarImagenes()" style="margin-top: 15px;">
                <i class="fas fa-redo"></i> Recargar imágenes
            </button>
        </div>
    </footer>

    <script>
        // Variables globales
        let imagenesFisica = Array(15).fill(null);
        let imagenesSm2 = Array(9).fill(null);
        let imagenesActuales = [];
        let indiceImagenActual = 0;
        
        // Inicializar las galerías al cargar la página
        document.addEventListener('DOMContentLoaded', function() {
            inicializarGaleria('fisica', 15);
            inicializarGaleria('sm2', 9);
            cargarImagenesAutomaticamente();
            actualizarContadores();
            
            // Configurar el visor de imágenes
            document.getElementById('cerrarVisor').addEventListener('click', cerrarVisor);
            document.getElementById('anteriorImg').addEventListener('click', imagenAnterior);
            document.getElementById('siguienteImg').addEventListener('click', imagenSiguiente);
            
            // Cerrar visor con tecla Escape
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape') cerrarVisor();
                if (e.key === 'ArrowLeft') imagenAnterior();
                if (e.key === 'ArrowRight') imagenSiguiente();
            });
        });
        
        // Inicializar una galería con contenedores vacíos
        function inicializarGaleria(materia, cantidad) {
            const galeria = document.getElementById(`galeria-${materia}`);
            galeria.innerHTML = '';
            
            for (let i = 0; i < cantidad; i++) {
                const contenedor = document.createElement('div');
                contenedor.className = 'imagen-container vacio';
                contenedor.dataset.indice = i;
                contenedor.dataset.materia = materia;
                
                contenedor.innerHTML = `
                    <i class="fas fa-plus icono-agregar"></i>
                    <div class="texto-agregar">Imagen no encontrada</div>
                `;
                
                contenedor.addEventListener('click', function(e) {
                    if (e.target.classList.contains('boton-eliminar')) return;
                    
                    if (!this.classList.contains('vacio')) {
                        abrirVisor(materia, i);
                    }
                });
                
                galeria.appendChild(contenedor);
            }
        }
        
        // Cargar imágenes automáticamente desde la carpeta
        function cargarImagenesAutomaticamente() {
            // Cargar imágenes de Física (IMG_1ENERGIA.jpg a IMG_15ENERGIA.jpg)
            for (let i = 1; i <= 15; i++) {
                const nombreArchivo = `IMG_${i}ENERGIA.jpg`;
                cargarImagenDesdeArchivo('fisica', i-1, nombreArchivo);
            }
            
            // Cargar imágenes de SM2 (IMG_1SM2.jpg a IMG_9SM2.jpg)
            for (let i = 1; i <= 9; i++) {
                const nombreArchivo = `IMG_${i}SM2.jpg`;
                cargarImagenDesdeArchivo('sm2', i-1, nombreArchivo);
            }
        }
        
        // Intentar cargar una imagen desde un archivo
        function cargarImagenDesdeArchivo(materia, indice, nombreArchivo) {
            const img = new Image();
            
            img.onload = function() {
                // La imagen existe, agregarla a la galería
                agregarImagen(materia, indice, img.src);
            };
            
            img.onerror = function() {
                // La imagen no existe, mantener el cuadro vacío
                console.log(`Imagen no encontrada: ${nombreArchivo}`);
            };
            
            // Intentar cargar la imagen
            img.src = nombreArchivo;
        }
        
        // Agregar una imagen a la galería
        function agregarImagen(materia, indice, src) {
            const contenedor = document.querySelector(`.imagen-container[data-materia="${materia}"][data-indice="${indice}"]`);
            
            // Actualizar el array correspondiente
            if (materia === 'fisica') {
                imagenesFisica[indice] = src;
            } else {
                imagenesSm2[indice] = src;
            }
            
            // Actualizar la interfaz
            contenedor.classList.remove('vacio');
            contenedor.innerHTML = `
                <img src="${src}" alt="Imagen ${materia} ${indice+1}">
            `;
            
            // Restaurar el evento click para abrir el visor
            contenedor.addEventListener('click', function(e) {
                if (e.target.classList.contains('boton-eliminar')) return;
                abrirVisor(materia, indice);
            });
            
            actualizarContadores();
            mostrarEstadoCargado();
        }
        
        // Recargar todas las imágenes
        function recargarImagenes() {
            // Limpiar arrays
            imagenesFisica = Array(15).fill(null);
            imagenesSm2 = Array(9).fill(null);
            
            // Reinicializar galerías
            inicializarGaleria('fisica', 15);
            inicializarGaleria('sm2', 9);
            
            // Volver a cargar imágenes
            cargarImagenesAutomaticamente();
            
            alert('Imágenes recargadas');
        }
        
        // Abrir el visor de imágenes
        function abrirVisor(materia, indice) {
            // Determinar qué array de imágenes usar
            imagenesActuales = materia === 'fisica' ? imagenesFisica : imagenesSm2;
            
            // Filtrar solo las imágenes que no son null
            const imagenesValidas = imagenesActuales.filter(img => img !== null);
            const indicesValidos = [];
            
            // Obtener los índices válidos
            imagenesActuales.forEach((img, idx) => {
                if (img !== null) indicesValidos.push(idx);
            });
            
            // Encontrar el índice actual en el array de índices válidos
            indiceImagenActual = indicesValidos.indexOf(indice);
            
            // Si no se encuentra la imagen, salir
            if (indiceImagenActual === -1) return;
            
            // Mostrar la imagen actual
            document.getElementById('imagenVisor').src = imagenesValidas[indiceImagenActual];
            document.getElementById('visor').style.display = 'flex';
            
            // Actualizar visibilidad de botones de navegación
            document.getElementById('anteriorImg').style.display = indiceImagenActual > 0 ? 'block' : 'none';
            document.getElementById('siguienteImg').style.display = indiceImagenActual < imagenesValidas.length - 1 ? 'block' : 'none';
        }
        
        // Cerrar el visor de imágenes
        function cerrarVisor() {
            document.getElementById('visor').style.display = 'none';
        }
        
        // Navegar a la imagen anterior en el visor
        function imagenAnterior() {
            if (indiceImagenActual > 0) {
                indiceImagenActual--;
                const imagenesValidas = imagenesActuales.filter(img => img !== null);
                document.getElementById('imagenVisor').src = imagenesValidas[indiceImagenActual];
                
                // Actualizar visibilidad de botones
                document.getElementById('anteriorImg').style.display = indiceImagenActual > 0 ? 'block' : 'none';
                document.getElementById('siguienteImg').style.display = 'block';
            }
        }
        
        // Navegar a la imagen siguiente en el visor
        function imagenSiguiente() {
            const imagenesValidas = imagenesActuales.filter(img => img !== null);
            if (indiceImagenActual < imagenesValidas.length - 1) {
                indiceImagenActual++;
                document.getElementById('imagenVisor').src = imagenesValidas[indiceImagenActual];
                
                // Actualizar visibilidad de botones
                document.getElementById('anteriorImg').style.display = 'block';
                document.getElementById('siguienteImg').style.display = indiceImagenActual < imagenesValidas.length - 1 ? 'block' : 'none';
            }
        }
        
        // Actualizar los contadores de imágenes
        function actualizarContadores() {
            const contadorFisica = imagenesFisica.filter(img => img !== null).length;
            const contadorSm2 = imagenesSm2.filter(img => img !== null).length;
            
            document.getElementById('contadorFisica').textContent = `${contadorFisica}/15 imágenes`;
            document.getElementById('contadorSm2').textContent = `${contadorSm2}/9 imágenes`;
            document.getElementById('contadorFooterFisica').textContent = contadorFisica;
            document.getElementById('contadorFooterSm2').textContent = contadorSm2;
        }
        
        // Mostrar mensaje de estado cargado
        function mostrarEstadoCargado() {
            const estado = document.getElementById('estadoGuardado');
            estado.style.display = 'block';
            setTimeout(() => {
                estado.style.display = 'none';
            }, 2000);
        }
    </script>
</body>
</html>