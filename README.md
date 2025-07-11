# 📰 n8nNews - Otomatik Teknoloji Haberleri Sunumu

Bu proje, RSS kaynaklarından teknoloji haberlerini otomatik olarak toplayıp, yapay zeka ile analiz ederek günlük HTML sunumları oluşturan bir **n8n workflow** sistemidir.

## 🚀 Özellikler

### 📊 **Otomatik Haber Toplama**
- 17 farklı RSS kaynağından anlık haber çekimi
- BBC, CNN, TechCrunch, The Guardian, NTV ve daha fazlası
- 24 saat filtresi ile sadece güncel haberler

### 🤖 **Yapay Zeka Destekli Analiz**
- Google Gemini 2.5 Pro ile akıllı haber seçimi
- 30 en ilginç haberin otomatik seçimi
- Türkçe çeviri ve yerelleştirme
- Kategorik önceliklendirme (AI, Teknoloji, Uzay, Enerji vb.)

### 🎨 **Profesyonel Sunum Oluşturma**
- Modern HTML reveal.js slide sunumları
- Slide numaralandırması (Slide 1, 2, 3...)
- Her slide'da haber kaynağı gösterimi
- RSS'den gelen gerçek görseller
- Responsive tasarım (mobil uyumlu)
- Hover efektleri ve animasyonlar

### ☁️ **Otomatik Kayıt ve Paylaşım**
- Google Drive'a otomatik yükleme
- Gmail ile günlük e-posta gönderimi
- HTML dosyası attachment olarak eklenir

### ⏰ **Zamanlanmış Çalışma**
- Her sabah 07:30'da otomatik çalışır
- Cron job benzeri schedule trigger

## 📁 Proje Yapısı

```
n8nNews/
├── n8n-docker/
│   ├── docker-compose.yml          # n8n Docker konfigürasyonu
│   ├── My workflow (2).json        # Ana workflow dosyası
│   └── n8n-data/                   # n8n verileri
│       ├── database.sqlite         # Workflow veritabanı
│       ├── config                  # n8n ayarları
│       └── nodes/                  # Özel node'lar
└── README.md                       # Bu dosya
```

## 🛠️ Kurulum

### Ön Gereksinimler
- Docker & Docker Compose
- Git

### 1. Projeyi Klonlayın
```bash
git clone https://github.com/yourusername/n8nNews.git
cd n8nNews/n8n-docker
```

### 2. n8n'i Başlatın
```bash
docker-compose up -d
```

### 3. n8n Arayüzüne Erişin
- Tarayıcıda `http://localhost:5678` adresine gidin
- İlk çalıştırmada kullanıcı hesabı oluşturun

### 4. Workflow'u İçe Aktarın
- n8n arayüzünde "Import from file" seçeneğini kullanın
- `My workflow (2).json` dosyasını yükleyin

### 5. Credential'ları Yapılandırın
Aşağıdaki servisler için API anahtarları gerekli:

#### Google Services
- **Google Gemini API**: [Google AI Studio](https://makersuite.google.com/app/apikey)
- **Google Drive API**: OAuth2 kimlik doğrulaması
- **Gmail API**: OAuth2 kimlik doğrulaması

#### Konfigürasyon
1. n8n'de "Credentials" bölümüne gidin
2. Her servis için gerekli bilgileri girin:
   - Google Gemini API Key
   - Google Drive OAuth2
   - Gmail OAuth2

## 🔧 Workflow Detayları

### RSS Kaynakları
- **NTV Teknoloji**: ntv.com.tr/teknoloji.rss
- **TechCrunch**: techcrunch.com/feed
- **CNET**: cnet.com/rss/news/
- **TechRadar**: techradar.com/feeds.xml
- **NY Times Tech**: nytimes.com/services/xml/rss/nyt/Technology.xml
- **BBC Technology**: feeds.bbci.co.uk/news/technology/rss.xml
- **The Guardian Tech**: theguardian.com/uk/technology/rss
- **CNN Technology**: rss.cnn.com/rss/edition_technology.rss
- Ve daha fazlası...

### Workflow Adımları
1. **RSS Read Nodes**: Paralel haber çekimi
2. **Merge Nodes**: Verileri birleştirme
3. **News Processor**: 24 saat filtresi ve veri temizleme
4. **AI Agent**: Gemini ile haber analizi ve seçimi
5. **HTML Processor**: Slide'ları oluşturma
6. **Binary Converter**: HTML'i dosya formatına çevirme
7. **Google Drive**: Buluta yükleme
8. **Gmail**: E-posta gönderimi

### Çıktı Formatı
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Teknoloji Haberleri - 11 Temmuz 2024</title>
    <!-- Reveal.js CSS/JS -->
  </head>
  <body>
    <div class="reveal">
      <div class="slides">
        <!-- Slide 1: İntro -->
        <!-- Slide 2-31: Haberler -->
        <!-- Slide 32: Trendler -->
      </div>
    </div>
  </body>
</html>
```

## 🎯 Kullanım Örnekleri

### Manuel Çalıştırma
- n8n arayüzünde workflow'u açın
- "Execute Workflow" butonuna tıklayın
- 2-3 dakika içinde Google Drive'da dosya hazır olur

### Otomatik Çalışma
- Her sabah 07:30'da otomatik çalışır
- E-postanıza günlük özet gönderilir
- Google Drive'da dosyalar birikir

### Özelleştirme
- **RSS Kaynakları**: Yeni RSS URL'leri ekleyebilirsiniz
- **AI Prompts**: Haber seçim kriterlerini değiştirebilirsiniz  
- **Tasarım**: CSS stillerini özelleştirebilirsiniz
- **Zamanlama**: Schedule trigger'ı değiştirebilirsiniz

## 🔐 Güvenlik

- API anahtarları n8n credentials'da şifrelenmiş olarak saklanır
- OAuth2 token'ları otomatik yenilenir
- RSS URL'leri güvenlik kontrolünden geçer
- HTML content escape edilir

## 🤝 Katkıda Bulunma

1. Fork edin
2. Feature branch oluşturun (`git checkout -b feature/amazing-feature`)
3. Commit yapın (`git commit -m 'Add amazing feature'`)
4. Push edin (`git push origin feature/amazing-feature`)
5. Pull Request oluşturun

## 📧 İletişim

- **Geliştirici**: Veli Kececi
- **E-posta**: vli.kcc@gmail.com
- **Proje**: [GitHub Repository](https://github.com/yourusername/n8nNews)

## 📄 Lisans

Bu proje MIT lisansı altında dağıtılmaktadır. Detaylar için `LICENSE` dosyasına bakın.

## 🙏 Teşekkürler

- **n8n**: Workflow automation platform
- **Google Gemini**: AI language model
- **Reveal.js**: HTML presentation framework
- **RSS Feed Providers**: Haber kaynakları

---

**⭐ Projeyi beğendiyseniz yıldız vermeyi unutmayın!** 