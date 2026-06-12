---
title: "Installing Java howto"
date: 2011-09-06
forum: Desktop Environments
---

### Post by COKEDUDE on 2011-09-06
A quick howto on installing both versions of java and choosing which version to use. 

Sun Java

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin sun-java6-fonts
```

Open Java

```
sudo apt-get install openjdk-6-jre
```

Configure which java you want. 

```
sudo update-java-alternatives -s java-6-sun
sudo update-alternatives --config java
```

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)
[http://www.clickonf5.org/7777/how-install-sun-java-ubuntu-1004-lts/](http://www.clickonf5.org/7777/how-install-sun-java-ubuntu-1004-lts/)

---

