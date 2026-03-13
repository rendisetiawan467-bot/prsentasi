# prsentasi<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sakti Presentasi - Pendidikan Agama Kristen & Budi Pekerti</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <style>
        :root {
            --primary-gold: #D4AF37;
            --deep-blue: #1e3a8a;
            --spiritual-gradient: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 50%, #D4AF37 100%);
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: #f8fafc;
        }
        
        .font-serif-display {
            font-family: 'Cormorant Garamond', serif;
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .holy-gradient {
            background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%);
        }
        
        .gold-accent {
            color: #D4AF37;
        }
        
        .slide-preview {
            aspect-ratio: 16/9;
            background: white;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            transition: transform 0.3s ease;
        }
        
        .slide-preview:hover {
            transform: translateY(-5px);
        }
        
        .drop-zone {
            border: 3px dashed #cbd5e1;
            transition: all 0.3s ease;
        }
        
        .drop-zone.drag-over {
            border-color: #D4AF37;
            background: rgba(212, 175, 55, 0.1);
        }
        
        .verse-decoration {
            position: relative;
        }
        
        .verse-decoration::before {
            content: '"';
            font-size: 4rem;
            position: absolute;
            top: -20px;
            left: -20px;
            color: #D4AF37;
            opacity: 0.3;
            font-family: 'Cormorant Garamond', serif;
        }
        
        .template-card {
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .template-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .template-card.selected {
            border: 3px solid #D4AF37;
            box-shadow: 0 0 0 4px rgba(212, 175, 55, 0.2);
        }
        
        .progress-bar {
            transition: width 0.5s ease;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        .cross-decoration {
            position: absolute;
            opacity: 0.05;
            pointer-events: none;
        }
        
        .slide-content {
            font-size: 0.6rem;
            line-height: 1.4;
        }
        
        @media (min-width: 768px) {
            .slide-content {
                font-size: 0.8rem;
            }
        }
        
        .scrollbar-hide::-webkit-scrollbar {
            display: none;
        }
        .scrollbar-hide {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 overflow-x-hidden">

    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass-effect border-b border-slate-200">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 holy-gradient rounded-lg flex items-center justify-center">
                        <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
                        </svg>
                    </div>
                    <div>
                        <h1 class="font-serif-display text-2xl font-bold text-slate-900">Sakti Presentasi</h1>
                        <p class="text-xs text-slate-500">Pendidikan Agama Kristen & Budi Pekerti</p>
                    </div>
                </div>
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#fitur" class="text-slate-600 hover:text-blue-900 transition">Fitur</a>
                    <a href="#materi" class="text-slate-600 hover:text-blue-900 transition">Materi</a>
                    <a href="#tentang" class="text-slate-600 hover:text-blue-900 transition">Tentang</a>
                    <button onclick="scrollToConverter()" class="bg-gradient-to-r from-blue-900 to-blue-700 text-white px-6 py-2 rounded-full hover:shadow-lg transition transform hover:scale-105">
                        Mulai Membuat
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative pt-32 pb-20 overflow-hidden">
        <div class="absolute inset-0 holy-gradient opacity-5"></div>
        <div class="absolute top-0 right-0 w-96 h-96 bg-yellow-400 rounded-full filter blur-3xl opacity-10 floating"></div>
        <div class="absolute bottom-0 left-0 w-72 h-72 bg-blue-400 rounded-full filter blur-3xl opacity-10 floating" style="animation-delay: 1.5s;"></div>
        
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="text-center max-w-4xl mx-auto">
                <div class="inline-block mb-4 px-4 py-1 rounded-full bg-blue-100 text-blue-800 text-sm font-medium border border-blue-200">
                    ✨ Berdasarkan Kurikulum Merdeka 2024
                </div>
                <h1 class="font-serif-display text-5xl md:text-7xl font-bold text-slate-900 mb-6 leading-tight">
                    Presentasi <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-900 to-blue-600">Rohani</span> yang Menginspirasi
                </h1>
                <p class="text-xl text-slate-600 mb-8 leading-relaxed">
                    Ubah materi Pendidikan Agama Kristen dan Budi Pekerti Anda menjadi presentasi yang indah dan bermakna. 
                    Dari PDF ke slide siap pakai dalam hitungan detik.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <button onclick="scrollToConverter()" class="bg-gradient-to-r from-blue-900 to-blue-700 text-white px-8 py-4 rounded-full text-lg font-semibold hover:shadow-xl transition transform hover:scale-105 flex items-center justify-center gap-2">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"></path></svg>
                        Unggah PDF Sekarang
                    </button>
                    <button onclick="showSample()" class="bg-white text-blue-900 border-2 border-blue-900 px-8 py-4 rounded-full text-lg font-semibold hover:bg-blue-50 transition flex items-center justify-center gap-2">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"></path></svg>
                        Lihat Contoh
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- Features Grid -->
    <section id="fitur" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="font-serif-display text-4xl font-bold text-slate-900 mb-4">Fitur Rohani</h2>
                <p class="text-slate-600 max-w-2xl mx-auto">Dirancang khusus untuk kebutuhan pendidikan agama Kristen dengan memperhatikan nilai-nilai spiritual dan estetika yang menyenangkan hati.</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <div class="p-8 rounded-2xl bg-gradient-to-br from-blue-50 to-white border border-blue-100 hover:shadow-xl transition">
                    <div class="w-14 h-14 bg-blue-900 rounded-xl flex items-center justify-center mb-6">
                        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path></svg>
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Ekstraksi PDF Cerdas</h3>
                    <p class="text-slate-600">Otomatis membaca dan menganalisis struktur materi dari file PDF Buku Guru atau Buku Siswa PAK.</p>
                </div>
                
                <div class="p-8 rounded-2xl bg-gradient-to-br from-yellow-50 to-white border border-yellow-100 hover:shadow-xl transition">
                    <div class="w-14 h-14 bg-yellow-600 rounded-xl flex items-center justify-center mb-6">
                        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Template Rohani</h3>
                    <p class="text-slate-600">Pilihan desain dengan nuansa spiritual, ayat emas, dan elemen visual yang menguatkan pesan iman.</p>
                </div>
                
                <div class="p-8 rounded-2xl bg-gradient-to-br from-blue-50 to-white border border-blue-100 hover:shadow-xl transition">
                    <div class="w-14 h-14 bg-blue-800 rounded-xl flex items-center justify-center mb-6">
                        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
                    </div>
                    <h3 class="text-xl font-bold text-slate-900 mb-3">Integrasi Alkitab</h3>
                    <p class="text-slate-600">Otomatis mendeteksi referensi ayat dan menambahkan konteks serta tampilan ayat yang menarik.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Main Converter Section -->
    <section id="converter" class="py-20 bg-slate-50 relative">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h2 class="font-serif-display text-4xl font-bold text-slate-900 mb-4">Buat Presentasi Anda</h2>
                <p class="text-slate-600">Ikuti langkah-langkah sederhana untuk mengubah materi menjadi presentasi rohani</p>
            </div>

            <!-- Step 1: Upload -->
            <div class="bg-white rounded-3xl shadow-xl p-8 mb-8 border border-slate-200">
                <div class="flex items-center mb-6">
                    <div class="w-10 h-10 rounded-full bg-blue-900 text-white flex items-center justify-center font-bold mr-4">1</div>
                    <h3 class="text-2xl font-bold text-slate-900">Unggah Materi PDF</h3>
                </div>
                
                <div id="dropZone" class="drop-zone rounded-2xl p-12 text-center cursor-pointer bg-slate-50">
                    <input type="file" id="pdfInput" accept=".pdf" class="hidden">
                    <div class="mb-4">
                        <svg class="w-16 h-16 mx-auto text-slate-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"></path>
                        </svg>
                    </div>
                    <p class="text-lg font-medium text-slate-700 mb-2">Seret file PDF ke sini atau klik untuk memilih</p>
                    <p class="text-sm text-slate-500">Mendukung Buku Guru, Buku Siswa, atau materi PAK lainnya (Maks. 10MB)</p>
                    <div id="fileInfo" class="hidden mt-4 p-4 bg-blue-50 rounded-lg border border-blue-200">
                        <p class="text-blue-900 font-medium" id="fileName"></p>
                        <p class="text-sm text-blue-600" id="fileSize"></p>
                    </div>
                </div>
            </div>

            <!-- Step 2: Template Selection -->
            <div class="bg-white rounded-3xl shadow-xl p-8 mb-8 border border-slate-200">
                <div class="flex items-center mb-6">
                    <div class="w-10 h-10 rounded-full bg-blue-900 text-white flex items-center justify-center font-bold mr-4">2</div>
                    <h3 class="text-2xl font-bold text-slate-900">Pilih Tema Presentasi</h3>
                </div>
                
                <div class="grid md:grid-cols-3 gap-6">
                    <div class="template-card rounded-xl overflow-hidden border-2 border-slate-200 selected" onclick="selectTemplate('classic', this)">
                        <div class="h-32 bg-gradient-to-br from-blue-900 to-blue-700 flex items-center justify-center">
                            <span class="text-white font-serif-display text-2xl">Klasik</span>
                        </div>
                        <div class="p-4">
                            <h4 class="font-bold text-slate-900">Elegan Klasik</h4>
                            <p class="text-sm text-slate-600 mt-1">Nuansa biru tua dan emas yang khusyuk dan formal</p>
                        </div>
                    </div>
                    
                    <div class="template-card rounded-xl overflow-hidden border-2 border-slate-200" onclick="selectTemplate('nature', this)">
                        <div class="h-32 bg-gradient-to-br from-green-700 to-emerald-500 flex items-center justify-center">
                            <span class="text-white font-serif-display text-2xl">Alam</span>
                        </div>
                        <div class="p-4">
                            <h4 class="font-bold text-slate-900">Ciptaan Allah</h4>
                            <p class="text-sm text-slate-600 mt-1">Tema alam untuk materi lingkungan dan ekologi</p>
                        </div>
                    </div>
                    
                    <div class="template-card rounded-xl overflow-hidden border-2 border-slate-200" onclick="selectTemplate('warm', this)">
                        <div class="h-32 bg-gradient-to-br from-orange-400 to-red-500 flex items-center justify-center">
                            <span class="text-white font-serif-display text-2xl">Hangat</span>
                        </div>
                        <div class="p-4">
                            <h4 class="font-bold text-slate-900">Kasih Karunia</h4>
                            <p class="text-sm text-slate-600 mt-1">Warna hangat untuk tema kasih dan komunitas</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Step 3: Generate -->
            <div class="bg-white rounded-3xl shadow-xl p-8 mb-8 border border-slate-200">
                <div class="flex items-center mb-6">
                    <div class="w-10 h-10 rounded-full bg-blue-900 text-white flex items-center justify-center font-bold mr-4">3</div>
                    <h3 class="text-2xl font-bold text-slate-900">Generate Presentasi</h3>
                </div>
                
                <div class="flex flex-col sm:flex-row gap-4 items-center justify-between bg-slate-50 p-6 rounded-xl">
                    <div>
                        <p class="text-slate-700 font-medium">Siap untuk membuat presentasi?</p>
                        <p class="text-sm text-slate-500">Sistem akan menganalisis struktur materi dan membuat slide otomatis</p>
                    </div>
                    <button onclick="generatePresentation()" id="generateBtn" class="bg-gradient-to-r from-blue-900 to-blue-700 text-white px-8 py-3 rounded-full font-semibold hover:shadow-lg transition transform hover:scale-105 disabled:opacity-50 disabled:cursor-not-allowed">
                        Generate Presentasi
                    </button>
                </div>

                <!-- Progress Bar -->
                <div id="progressContainer" class="hidden mt-6">
                    <div class="flex justify-between text-sm text-slate-600 mb-2">
                        <span>Menganalisis materi...</span>
                        <span id="progressPercent">0%</span>
                    </div>
                    <div class="w-full bg-slate-200 rounded-full h-2">
                        <div id="progressBar" class="progress-bar bg-gradient-to-r from-blue-900 to-yellow-600 h-2 rounded-full" style="width: 0%"></div>
                    </div>
                </div>
            </div>

            <!-- Results Section -->
            <div id="resultsSection" class="hidden">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="text-2xl font-bold text-slate-900">Hasil Presentasi</h3>
                    <div class="flex gap-3">
                        <button onclick="downloadPPT()" class="bg-green-600 text-white px-6 py-2 rounded-full hover:bg-green-700 transition flex items-center gap-2">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path></svg>
                            Unduh PPT
                        </button>
                        <button onclick="downloadPDF()" class="bg-red-600 text-white px-6 py-2 rounded-full hover:bg-red-700 transition flex items-center gap-2">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path></svg>
                            Unduh PDF
                        </button>
                    </div>
                </div>

                <div id="slidesContainer" class="grid gap-8">
                    <!-- Slides will be generated here -->
                </div>
            </div>
        </div>
    </section>

    <!-- Curriculum Content Reference -->
    <section id="materi" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="font-serif-display text-4xl font-bold text-slate-900 mb-4">Materi Kurikulum</h2>
                <p class="text-slate-600">Berbasis Kurikulum Merdeka Pendidikan Agama Kristen dan Budi Pekerti</p>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-blue-900 to-blue-800 p-6 text-white hover:shadow-2xl transition">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-white opacity-5 rounded-full -mr-16 -mt-16"></div>
                    <div class="relative z-10">
                        <div class="text-4xl mb-4">✨</div>
                        <h3 class="font-bold text-xl mb-2">Allah Berkarya</h3>
                        <p class="text-blue-100 text-sm">Tuhan Pencipta, Pemelihara, Penyelamat, dan Pembaru. Memahami sifat dan karya Allah dalam kehidupan.</p>
                    </div>
                </div>

                <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-indigo-800 to-purple-900 p-6 text-white hover:shadow-2xl transition">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-white opacity-5 rounded-full -mr-16 -mt-16"></div>
                    <div class="relative z-10">
                        <div class="text-4xl mb-4">🙏</div>
                        <h3 class="font-bold text-xl mb-2">Manusia & Nilai Kristiani</h3>
                        <p class="text-indigo-100 text-sm">Hakikat manusia sebagai ciptaan Allah, dosa, keselamatan, dan panggilan hidup kudus.</p>
                    </div>
                </div>

                <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-emerald-700 to-teal-800 p-6 text-white hover:shadow-2xl transition">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-white opacity-5 rounded-full -mr-16 -mt-16"></div>
                    <div class="relative z-10">
                        <div class="text-4xl mb-4">⛪</div>
                        <h3 class="font-bold text-xl mb-2">Gereja & Masyarakat</h3>
                        <p class="text-emerald-100 text-sm">Hidup bergereja, bermasyarakat, moderasi beragama, dan kontribusi warga negara.</p>
                    </div>
                </div>

                <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-amber-600 to-orange-700 p-6 text-white hover:shadow-2xl transition">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-white opacity-5 rounded-full -mr-16 -mt-16"></div>
                    <div class="relative z-10">
                        <div class="text-4xl mb-4">🌿</div>
                        <h3 class="font-bold text-xl mb-2">Alam & Lingkungan</h3>
                        <p class="text-amber-100 text-sm">Teologi lingkungan, tanggung jawab menjaga ciptaan, dan ekologi Kristen.</p>
                    </div>
                </div>
            </div>

            <div class="mt-12 bg-slate-50 rounded-2xl p-8 border border-slate-200">
                <h3 class="font-serif-display text-2xl font-bold text-slate-900 mb-4">Nilai-Nilai Budi Pekerti Kristen</h3>
                <div class="grid md:grid-cols-3 gap-6">
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">1</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Kasih (Agape)</h4>
                            <p class="text-sm text-slate-600">Mencintai sesama tanpa syarat, bahkan musuh sekalipun</p>
                        </div>
                    </div>
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">2</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Integritas</h4>
                            <p class="text-sm text-slate-600">Konsisten antara iman, perkataan, dan perbuatan</p>
                        </div>
                    </div>
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">3</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Kerendahan Hati</h4>
                            <p class="text-sm text-slate-600">Mengutamakan kepentingan orang lain di atas diri sendiri</p>
                        </div>
                    </div>
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">4</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Tanggung Jawab</h4>
                            <p class="text-sm text-slate-600">Setia dalam talenta dan panggilan masing-masing</p>
                        </div>
                    </div>
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">5</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Keadilan</h4>
                            <p class="text-sm text-slate-600">Membela yang tertindas dan memberi hak yang sewajarnya</p>
                        </div>
                    </div>
                    <div class="flex items-start space-x-3">
                        <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center flex-shrink-0 mt-1">
                            <span class="text-blue-800 font-bold text-sm">6</span>
                        </div>
                        <div>
                            <h4 class="font-semibold text-slate-900">Pengampunan</h4>
                            <p class="text-sm text-slate-600">Memaafkan sebagaimana Kristus telah mengampuni kita</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-slate-900 text-white py-12 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-3 gap-8">
                <div>
                    <h3 class="font-serif-display text-2xl font-bold mb-4">Sakti Presentasi</h3>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Alat bantu digital untuk pendidik agama Kristen dalam menyampaikan materi pembelajaran yang bermakna dan menginspirasi generasi muda.
                    </p>
                </div>
                <div>
                    <h4 class="font-semibold mb-4">Referensi</h4>
                    <ul class="space-y-2 text-sm text-slate-400">
                        <li>Kurikulum Merdeka PAK 2024</li>
                        <li>Buku Guru Pendidikan Agama Kristen</li>
                        <li>Alkitab Terjemahan Baru</li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-semibold mb-4">Ayat Motivasi</h4>
                    <blockquote class="verse-decoration text-slate-300 text-sm italic pl-4 border-l-2 border-yellow-600">
                        "Jadikanlah hatiku bersih, ya Allah, dan perbaruilah semangatku yang tekun."
                        <br><span class="text-yellow-600 not-italic font-semibold mt-1 block">— Mazmur 51:12</span>
                    </blockquote>
                </div>
            </div>
            <div class="mt-8 pt-8 border-t border-slate-800 text-center text-slate-500 text-sm">
                <p>&copy; 2024 Sakti Presentasi. Dibuat untuk kemuliaan Tuhan.</p>
            </div>
        </div>
    </footer>

    <script>
        // Initialize PDF.js
        pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
        
        let currentFile = null;
        let extractedText = '';
        let selectedTemplate = 'classic';
        let generatedSlides = [];

        // Drag and Drop functionality
        const dropZone = document.getElementById('dropZone');
        const pdfInput = document.getElementById('pdfInput');

        dropZone.addEventListener('click', () => pdfInput.click());
        
        dropZone.addEventListener('dragover', (e) => {
            e.preventDefault();
            dropZone.classList.add('drag-over');
        });

        dropZone.addEventListener('dragleave', () => {
            dropZone.classList.remove('drag-over');
        });

        dropZone.addEventListener('drop', (e) => {
            e.preventDefault();
            dropZone.classList.remove('drag-over');
            const files = e.dataTransfer.files;
            if (files.length > 0 && files[0].type === 'application/pdf') {
                handleFile(files[0]);
            }
        });

        pdfInput.addEventListener('change', (e) => {
            if (e.target.files.length > 0) {
                handleFile(e.target.files[0]);
            }
        });

        function handleFile(file) {
            currentFile = file;
            document.getElementById('fileInfo').classList.remove('hidden');
            document.getElementById('fileName').textContent = file.name;
            document.getElementById('fileSize').textContent = (file.size / 1024 / 1024).toFixed(2) + ' MB';
            
            // Read PDF
            const reader = new FileReader();
            reader.onload = async function(e) {
                const typedarray = new Uint8Array(e.target.result);
                try {
                    const pdf = await pdfjsLib.getDocument(typedarray).promise;
                    let fullText = '';
                    
                    for (let i = 1; i <= Math.min(pdf.numPages, 10); i++) {
                        const page = await pdf.getPage(i);
                        const textContent = await page.getTextContent();
                        const pageText = textContent.items.map(item => item.str).join(' ');
                        fullText += pageText + ' ';
                    }
                    
                    extractedText = fullText;
                    console.log('Text extracted:', extractedText.substring(0, 500));
                } catch (error) {
                    console.error('Error reading PDF:', error);
                    alert('Terjadi kesalahan saat membaca PDF. Pastikan file tidak terenkripsi.');
                }
            };
            reader.readAsArrayBuffer(file);
        }

        function selectTemplate(template, element) {
            selectedTemplate = template;
            document.querySelectorAll('.template-card').forEach(card => {
                card.classList.remove('selected');
            });
            element.classList.add('selected');
        }

        function scrollToConverter() {
            document.getElementById('converter').scrollIntoView({ behavior: 'smooth' });
        }

        function showSample() {
            // Create sample presentation data
            extractedText = "SAMPLE: Pendidikan Agama Kristen. Tuhan Yesus Kristus adalah Tuhan dan Juruselamat. Kasih Allah begitu besar sehingga mengaruniakan Anak-Nya yang tunggal. Manusia diciptakan menurut gambar dan rupa Allah. Gereja adalah tubuh Kristus. Alam semesta diciptakan oleh Allah dan merupakan anugerah-Nya.";
            currentFile = { name: "Contoh_Materi_PAK.pdf" };
            
            document.getElementById('fileInfo').classList.remove('hidden');
            document.getElementById('fileName').textContent = "Contoh_Materi_PAK.pdf";
            document.getElementById('fileSize').textContent = "Contoh data";
            
            generatePresentation();
        }

        async function generatePresentation() {
            if (!currentFile) {
                alert('Silakan unggah file PDF terlebih dahulu!');
                return;
            }

            const btn = document.getElementById('generateBtn');
            const progressContainer = document.getElementById('progressContainer');
            const progressBar = document.getElementById('progressBar');
            const progressPercent = document.getElementById('progressPercent');
            
            btn.disabled = true;
            btn.textContent = 'Memproses...';
            progressContainer.classList.remove('hidden');
            
            // Simulate progress
            let progress = 0;
            const interval = setInterval(() => {
                progress += Math.random() * 15;
                if (progress > 100) progress = 100;
                progressBar.style.width = progress + '%';
                progressPercent.textContent = Math.round(progress) + '%';
                
                if (progress === 100) {
                    clearInterval(interval);
                    setTimeout(() => {
                        createSlides();
                        progressContainer.classList.add('hidden');
                        btn.disabled = false;
                        btn.textContent = 'Generate Presentasi';
                        document.getElementById('resultsSection').classList.remove('hidden');
                        document.getElementById('resultsSection').scrollIntoView({ behavior: 'smooth' });
                    }, 500);
                }
            }, 200);
        }

        function createSlides() {
            const container = document.getElementById('slidesContainer');
            container.innerHTML = '';
            
            // Parse content and create slides based on template
            const slides = parseContentToSlides(extractedText);
            generatedSlides = slides;
            
            slides.forEach((slide, index) => {
                const slideEl = createSlideElement(slide, index + 1, slides.length);
                container.appendChild(slideEl);
            });
        }

        function parseContentToSlides(text) {
            // Smart parsing logic for PAK content
            const slides = [];
            
            // Title Slide
            slides.push({
                type: 'title',
                title: extractTitle(text) || 'Pendidikan Agama Kristen',
                subtitle: 'Materi Pembelajaran',
                verse: 'Amsal 1:7',
                verseText: 'Takut akan Tuhan adalah permulaan pengetahuan'
            });
            
            // Content detection
            const sections = detectSections(text);
            
            sections.forEach((section, idx) => {
                if (section.length > 50) {
                    slides.push({
                        type: 'content',
                        title: extractHeading(section) || `Materi ${idx + 1}`,
                        content: section.substring(0, 300) + (section.length > 300 ? '...' : ''),
                        bullets: extractKeyPoints(section),
                        reference: extractBibleReference(section)
                    });
                }
            });
            
            // Add closing slide if not enough content
            if (slides.length < 3) {
                slides.push({
                    type: 'content',
                    title: 'Pokok-Pokok Pembelajaran',
                    content: 'Materi Pendidikan Agama Kristen membahas tentang iman, nilai-nilai Kristiani, dan aplikasinya dalam kehidupan sehari-hari.',
                    bullets: [
                        'Memahami konsep dasar kekristenan',
                        'Mengaplikasikan nilai-nilai Kristiani',
                        'Menghayati ajaran Alkitab'
                    ]
                });
                
                slides.push({
                    type: 'closing',
                    title: 'Renungan',
                    content: 'Kiranya pembelajaran ini memperkuat iman kita dan membuat kita semakin serupa dengan Kristus.',
                    verse: '2 Korintus 3:18',
                    verseText: 'Dan kita semua mencerminkan kemuliaan Tuhan dengan muka yang tidak berselubung.'
                });
            }
            
            return slides;
        }

        function detectSections(text) {
            // Split by common delimiters
            const delimiters = /(?:Bab|Bagian|\.|\n\n)+/;
            return text.split(delimiters).filter(s => s.trim().length > 30);
        }

        function extractTitle(text) {
            const match = text.match(/Pendidikan.*Kristen|PAK|Agama.*Kristen/i);
            return match ? match[0] : null;
        }

        function extractHeading(text) {
            const sentences = text.split(/[.!?]+/).filter(s => s.length > 10);
            return sentences[0] ? sentences[0].substring(0, 50) : 'Materi Pembelajaran';
        }

        function extractKeyPoints(text) {
            const sentences = text.split(/[.!?]+/).filter(s => s.length > 20 && s.length < 100);
            return sentences.slice(0, 3).map(s => s.trim());
        }

        function extractBibleReference(text) {
            const pattern = /\b(?:Kejadian|Keluaran|Imamat|Bilangan|Ulangan|Yosua|Hakim-hakim|Rut|1 Samuel|2 Samuel|1 Raja-raja|2 Raja-raja|Mazmur|Amsal|Pengkhotbah|Yesaya|Yeremia|Yehezkiel|Daniel|Hosea|Yoel|Amos|Obaja|Yunus|Mikha|Nahum|Habakuk|Zefanya|Hagai|Zakharia|Maleakhi|Matius|Markus|Lukas|Yohanes|Kisah|Roma|1 Korintus|2 Korintus|Galatia|Efesus|Filipi|Kolose|1 Tesalonika|2 Tesalonika|1 Timotius|2 Timotius|Titus|Filemon|Ibrani|Yakobus|1 Petrus|2 Petrus|1 Yohanes|2 Yohanes|3 Yohanes|Yudas|Wahyu)\s+\d+[:]\d+(?:-\d+)?\b/gi;
            const matches = text.match(pattern);
            return matches ? matches[0] : null;
        }

        function createSlideElement(slide, number, total) {
            const div = document.createElement('div');
            div.className = 'bg-white rounded-2xl shadow-lg overflow-hidden border border-slate-200';
            
            let bgClass, textClass, accentClass;
            
            switch(selectedTemplate) {
                case 'nature':
                    bgClass = 'bg-gradient-to-br from-green-800 to-emerald-600';
                    textClass = 'text-white';
                    accentClass = 'text-emerald-200';
                    break;
                case 'warm':
                    bgClass = 'bg-gradient-to-br from-orange-500 to-red-600';
                    textClass = 'text-white';
                    accentClass = 'text-orange-200';
                    break;
                default: // classic
                    bgClass = 'bg-gradient-to-br from-blue-900 via-blue-800 to-blue-900';
                    textClass = 'text-white';
                    accentClass = 'text-yellow-400';
            }
            
            let content = '';
            
            if (slide.type === 'title') {
                content = `
                    <div class="slide-preview ${bgClass} ${textClass} p-8 md:p-12 flex flex-col justify-center items-center text-center relative overflow-hidden">
                        <div class="absolute top-0 left-0 w-full h-full opacity-10">
                            <svg class="w-full h-full" viewBox="0 0 100 100" preserveAspectRatio="none">
                                <path d="M0,0 L100,100 M100,0 L0,100" stroke="white" stroke-width="0.5"/>
                            </svg>
                        </div>
                        <div class="relative z-10">
                            <div class="text-6xl mb-6">✝</div>
                            <h2 class="font-serif-display text-3xl md:text-5xl font-bold mb-4 leading-tight">${slide.title}</h2>
                            <p class="text-xl ${accentClass} mb-8">${slide.subtitle}</p>
                            <div class="mt-8 pt-8 border-t border-white/20">
                                <p class="text-sm opacity-80 italic">"${slide.verseText}"</p>
                                <p class="text-xs ${accentClass} mt-1">— ${slide.verse}</p>
                            </div>
                        </div>
                    </div>
                `;
            } else if (slide.type === 'closing') {
                content = `
                    <div class="slide-preview ${bgClass} ${textClass} p-8 md:p-12 flex flex-col justify-center items-center text-center">
                        <h3 class="font-serif-display text-3xl font-bold mb-6">${slide.title}</h3>
                        <p class="text-lg opacity-90 mb-8 max-w-2xl">${slide.content}</p>
                        <div class="bg-white/10 rounded-xl p-6 max-w-xl">
                            <p class="italic text-lg mb-2">"${slide.verseText}"</p>
                            <p class="${accentClass} text-sm">— ${slide.verse}</p>
                        </div>
                    </div>
                `;
            } else {
                const bullets = slide.bullets ? slide.bullets.map(b => `<li class="flex items-start gap-2 mb-2"><span class="${accentClass} mt-1">•</span><span>${b}</span></li>`).join('') : '';
                
                content = `
                    <div class="slide-preview ${bgClass} ${textClass} p-8 md:p-12 flex flex-col">
                        <div class="flex-1">
                            <h3 class="font-serif-display text-2xl md:text-3xl font-bold mb-6 border-b border-white/20 pb-4">${slide.title}</h3>
                            <p class="text-base md:text-lg opacity-90 mb-6 leading-relaxed">${slide.content}</p>
                            ${bullets ? `<ul class="space-y-2 text-sm md:text-base opacity-90">${bullets}</ul>` : ''}
                        </div>
                        ${slide.reference ? `<div class="mt-6 pt-4 border-t border-white/20 text-right"><span class="text-xs ${accentClass}">📖 ${slide.reference}</span></div>` : ''}
                    </div>
                `;
            }
            
            div.innerHTML = `
                <div class="p-4 bg-slate-50 border-b border-slate-200 flex justify-between items-center">
                    <span class="text-sm font-medium text-slate-600">Slide ${number} dari ${total}</span>
                    <div class="flex gap-2">
                        <button onclick="editSlide(${number-1})" class="text-xs bg-white border border-slate-300 px-3 py-1 rounded hover:bg-slate-100 transition">Edit</button>
                        <button onclick="deleteSlide(${number-1})" class="text-xs bg-red-50 text-red-600 border border-red-200 px-3 py-1 rounded hover:bg-red-100 transition">Hapus</button>
                    </div>
                </div>
                ${content}
            `;
            
            return div;
        }

        function editSlide(index) {
            const newTitle = prompt('Edit judul slide:', generatedSlides[index].title);
            if (newTitle) {
                generatedSlides[index].title = newTitle;
                createSlides();
            }
        }

        function deleteSlide(index) {
            if (confirm('Hapus slide ini?')) {
                generatedSlides.splice(index, 1);
                createSlides();
            }
        }

        function downloadPPT() {
            alert('Fitur unduh PPT akan menghasilkan file .pptx yang dapat diedit di PowerPoint. [Simulasi: File akan diunduh]');
        }

        function downloadPDF() {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF('l', 'mm', 'a4');
            
            // Simple PDF generation simulation
            doc.setFillColor(30, 58, 138);
            doc.rect(0, 0, 297, 210, 'F');
            
            doc.setTextColor(255, 255, 255);
            doc.setFontSize(30);
            doc.text('Presentasi PAK', 148, 105, { align: 'center' });
            
            doc.setFontSize(12);
            doc.setTextColor(212, 175, 55);
            doc.text('Generated by Sakti Presentasi', 148, 120, { align: 'center' });
            
            doc.save('Presentasi_PAK.pdf');
        }

        // Add smooth scrolling for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });
    </script>
</body>
</html>
