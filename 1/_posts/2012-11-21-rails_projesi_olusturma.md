---
layout: post
title: Yeni Bir Rails Projesi Oluşturma
---

#Rails Kurulumu

Rails kurmanın en kolay yolu RubyGems avantajını kullanmaktır. Genellikle bu komutu root 
kullanıcı olarak çalıştırmanız gerekir.

    # gem install rails

veya

    $ sudo gem install rails

komutları ile sisteminize rails' i yükleyebilirsiniz.

Eğerki sisteminizde rails varsa,

    $ rails -v 
    Rails 3.2.8

veya 

    $ rails --version
    Rails 3.2.8

komutları ile sürümünüzü öğrenebilirsiniz.

Eğerki Windows işletim sistemi kullanıyorsanız [Ruby On Rails](http://railsinstaller.org/)
adresinden yardım alarak yapabilirsiniz.

#Blog Uygulaması Üretmek

Konsoldan üzerinde çalışmak istediğimiz bir klasör veya ev dizinimizde 

    $ rails new blog

komutunu veriyoruz.Bu komuttan sonra rails gerekli klasör ve dosyaların
bulunduğu bir blog klasörü oluşturuyor. 

Daha sonra;

    $ cd blog

komutu ile blog uygulamamızın içerisine giriyoruz. 

**Not:** Aksi söylenmedikçe yapılan işlemler blog uygulamasının içindeyken yapılacaktır.

Oluşturulan blog uygulamsında bulunan dosya/klasör ve amaçlarından kısaca
bahsedelim:

**app/**        --> models, views, controllers, assets ve helpers gibi klasörleri
içerir.

**config/**     --> Uygulamanızın çalışma kuralları, yönlendirmeler ve veritabanı
ayarlamaları bu klasörde bulunur.

**config.ru**   --> Rack temelli uygulamalarda, uygulamayı başlatma yarayan konfigürasyonlardır.

**db/**         --> Veritabanı şemalarını ve migrasyonları içermektedir.

**doc/**        --> Uygulamanızın dökümanlarını bu klasörün içindedir.

**Gemfile**     --> Rails uygulamanızın hangi Gemlere bağlı olduğunu göstermektedir

**lib/**        --> Uygulamanız için gemişletilmiş modüller burada bulunmaktadır.

**log/**        --> Uygulamanızın log dosyaları burada tutulur.

**public/**     --> Statik dosyaları ve derlenmiş assets dosyalarını barındırır.

**Rakefile**    --> Bu dosyada terminalden çalıştırılabilen batch işleri bulunmaktadır.

**README.rdoc** --> README dosyası uygulamanız hakkında kısa bilgiler bulundurmaya
yarar.

**script/**     --> Başlangıç uygulamanızın rails script dosyalarını içermektedir.

**test/**       --> Rails uygulamasının test konuları bu kısımda bulunmaktadır.

**tmp/**        --> Geçici dosyaların bulunduğu kısımdır.

**vendor/**     --> 3. parti kodlar burada bulunmaktadır. Tipik bir rails
uygulaması, Ruby Gemleri, Rails kodlarını içermektedir.

#Veritabanı Konfigürasyonu

Tüm Rails uygulamaları bir veritabanı kullanmaktadır. Kullanılacak bu veritabanı
config/database.yml dosyasında tarif edilmektedir.

**1.** SQLite3 Veritabanı Konfigürasyonu

Yeni bir Rails uygulaması oluşturduğunuzda default olarak SQLite3 veritabanı ile karşılaşırsınız.

SQLite3 ile çalışacaksak config/database.yml içine;

    development:
     adapter: sqlite3
     database: db/development.sqlite3
     pool: 5
     timeout: 5000

bilgilerini ekleriz.

**2.** MySQL Veritabanı Konfigürasyonu

MySQL veritabanı kullanmak isterseniz config/database.yml içine;

    development:
     adapter: mysql2
     encoding: utf8
     database: blog_development
     pool: 5
     username: root
     password:
     socket: /tmp/mysql.sock

bilgilerini eklemeniz gereklidir.

**3.** PostgreSQL Veritabanı Konfigürasyonu

PostgreSQL veritabanı kullanmak isterseniz config/database.yml içine;

    development:
     adapter: postgresql
     encoding: unicode
     database: blog_development
     pool: 5
     username: blog
     password:

bilgilerini eklemeniz gereklidir.

- Veritabanı konfigürasyonlarını tamamladıktan sonra Rails' in boş bir veritabanı
üretmesini sağlamamız gerekli. Bunun için konsoldan; 

$ rake db:create

komutunu veriyoruz. Bu komut bize db/ klasörü altında geliştirme ve test
veritabanları oluşturuyor.


