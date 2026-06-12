---
title: "sqldeveloper installtion issues in 19.04"
date: 2019-06-24
forum: Desktop Environments
---

### Post by AlphA_ZA on 2019-06-24
Hi,

I recently installed Ubuntu 19.04 on my laptop and all is going well except that I cannot get sqldeveloper to work. When I try to use the default java-11-openjdk-amd64, I get the following error

```


Type the full pathname of a JDK installation (or Ctrl-C to quit), the path will be stored in /home/derrick/.sqldeveloper/19.1.0/product.conf
/usr/lib/jvm/java-1.11.0-openjdk-amd64

Found /usr/lib/jvm/java-8-openjdk-amd64/bin/java to run this product, and the major version of this Java is 11.
The mandatory minimum major version to run this product is 1.8.
This product cannot run with this Java.

Error: /usr/lib/jvm/java-1.11.0-openjdk-amd64/bin/java not found or not a valid JDK


```

So, I removed JDK 11 and installed JDK 1.8. After doing this, sqldeveloper starts, however , after opening, it says that it cannot continue as JavaFX is not installed. Problem with that is that I cannot find openjx for JDK 8 anywhere. The default for 19.04 is openjfx 11. So I am kind going round in circles here.


Does anybody have any guidance/advice on how I can get this to wotk on 19.04?

---

