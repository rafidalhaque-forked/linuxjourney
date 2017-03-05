# ماژول‌های کرنل

## محتویات درس

من یک ماشین دوست‌داشتنی دارم. کلی پول و وقت صرف سر هم کردن این ماشین کردم. یک اسپویلر، آویزِ چرخ، و کمی متعلقات دیگر. این اضافات، کارکرد اصلی ماشین را تغییر نمی‌دهد و من می‌توانم آن‌ها را به راحتی از ماشین جدا کنم. کرنل نیز با وجود ماژول‌های کرنل از راه‌کاری مشابه بهره می‌برد.

کرنل به خودی خود، یک نرم‌افزار یکپارچه و یک‌تکه است. زمانی که می‌خواهیم پشتیبانی از یک کیبورد جدید را اضافه کنیم، کد شناسایی کیبورد را مستقیماً به کد کرنل اضافه نمی‌کنیم. دقیقاً مثل زمانی که یک آویز دوچرخه را به ماشین جوش نمی‌دهیم (یا شاید هم شما جوش می‌دهید!؟ پیچ و مهره را از شما گرفته‌اند مگر!؟). ماژول‌های کرنل کدهایی هستند که می‌توانند بنا به خواست شما بر روی کرنل سوار یا جدا شوند. ماژول‌ها به ما اجاره می‌دهند که عمل‌کرد کرنل را بدون اینکه نیازی به اضافه کردن کد به هسته‌ی اصلی کرنل باشد، گسترش دهیم. ما در اکثر مواقع می‌توانیم ماژول‌ها را بدون اینکه نیازی به راه‌اندازی مجدد سیستم باشد به هسته اضافه کنیم.

**نگاهی به لیست ماژول‌های جاریِ لود شده**

***$ lsmod***

**لود یا بارگیری یک ماژول**

**$ sudo modprobe bluetooth**

Modprobe سعی می‌کند ماژول مورد نظر را از **/lib/modules/(kernel version)/kernel/drivers/** لود کند. ماژول‌های هسته ممکن است که پیش‌نیازهایی نیز داشته باشند. در این حالت modprobe ماژولِ ما به همراه پیش‌نیازهایش (اگر لود نشده‌اند) با هم لود می‌کند.

**حذف یک ماژول**

```$ sudo modprobe -r bluetooth```

**لود در زمان راه‌اندازی سیستم**

شما همچنین می‌توانید ماژول‌ها را در حین راه‌اندازی سیستم لود کنید. این کار نیاز به لود کردن موقت ماژول توسط modprobe را برطرف می‌کند. زمانی که از modprobe استفاده می‌کنید، ماژول بعد از ری‌استارت پیاده یا آن‌لود می‌شود. فقط کافیست که دایرکتوری ‎/etc/modprobe.d را دستکاری کرده و فایل پیکربندی را به این صورت به آن اضافه کنید:

```
pete@icebox:~$ /etc/modprobe.d/peanutbutter.conf

options peanut_butter type=almond
```

مثالِ عجیب غریبی بود ولی خب یک ماژول با اسم peanut_butter دارید و می‌خواهید که پارامتر هسته برای type=almond را به آن اضافه کنید. و اکنون شما این پیکربندی جدید را در حین راه‌اندازی سیستم بارگیری می‌کنید. همچنین به خاطر داشته باشید که ماژول‌های کرنل پارامترهای کرنل مخصوص به خود را دارند.

**در هنگام راه‌اندازی ماژول را لود نکن**

با اضافه کردن یک فایل پیکربندی شبیه به فایل زیر می‌توانید اطمینان حاصل کنید که یک ماژول در حین راه‌اندازی سیستم، لود نمی‌شود:

```
pete@icebox:~$ /etc/modprobe.d/peanutbutter.conf

blacklist peanut_butter
```

## تمرین

ماژول بلوتوث خود را با modprobe آن‌لود کنید و ببینید چه اتفاقی می‌افتد. چطور درستش می‌کنید؟

## سؤال آزمون

چه دستوری برای آن‌لود کردن یک ماژول مورد استفاده قرار می‌گیرد.

## پاسخ آزمون

modprobe -r