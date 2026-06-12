---
title: "L'open wengo se'm queda penjat."
date: 2007-12-08
forum: Catalan Team
---

### Post by lo gambusí on 2007-12-08
Salut!

He instal·lat l'open wengo, i a l'hora de posar-lo en marxa, la primera vegada se'm va encendre perfectament. La segona, però, se'm queda pensant l'ordinador i ja no s'obre. He provat de fer-ho des de la consola i me diu això:

> oriol@oriol-laptop:~$ qtwengophone
(info) 17:58:19 Wenbox::Wenbox(): Wenbox dll not loaded
(debug) 17:58:19 int main(int, char**): WengoPhone started
(debug) 17:58:19 virtual void WebcamDriver::cleanup(): Cleaning up the Meta webcam driver
(debug) 17:58:19 virtual bool FileReader::open(): loading /home/oriol/.wengophone/config.xml
(debug) 17:58:19 virtual bool FileWriter::open(): saving to /home/oriol/.wengophone/config.xml
(debug) 17:58:19 virtual bool FileReader::open(): loading /home/oriol/.wengophone/config.xml
(debug) 17:58:19 QtWengoStyle::QtWengoStyle(): style=cleanlooks
(debug) 17:58:19 virtual void QtFactory::reset():  RESET 
bind: Address already in use
(debug) 17:58:29 bool ServerSocket::createMainListeningSocket(): cannot bind main socket
(info) 17:58:29 void QtLanguage::loadLanguageFromConfig(): no Qt translation available for locale ''
(debug) 17:58:29 void QtLanguage::loadLanguageFromConfig(): 
(info) 17:58:29 void QtLanguage::loadLanguageFromConfig(): no application translation available for locale ''
Signal catched: SIGCHLD
QProcess: Destroyed while process is still running.
(debug) 17:58:39 virtual void NetworkProxyDiscovery::run(): discovering network proxy...
(debug) 17:58:39 virtual void NetworkProxyDiscovery::run(): searching for proxy...
(debug) 17:58:39 virtual void NetworkProxyDiscovery::run(): no proxy found
oriol@oriol-laptop:~$ 


:confused:

---

### Post by papapep on 2007-12-08
> oriol@oriol-laptop:~$ qtwengophone
(info) 17:58:19 Wenbox::Wenbox(): Wenbox dll not loaded
(debug) 17:58:19 int main(int, char**): WengoPhone started
(debug) 17:58:19 virtual void WebcamDriver::cleanup(): Cleaning up the Meta webcam driver
(debug) 17:58:19 virtual bool FileReader:pen(): loading /home/oriol/.wengophone/config.xml
(debug) 17:58:19 virtual bool FileWriter:pen(): saving to /home/oriol/.wengophone/config.xml
(debug) 17:58:19 virtual bool FileReader:pen(): loading /home/oriol/.wengophone/config.xml
(debug) 17:58:19 QtWengoStyle::QtWengoStyle(): style=cleanlooks
(debug) 17:58:19 virtual void QtFactory::reset(): RESET
bind: Address already in use
(debug) 17:58:29 bool ServerSocket::createMainListeningSocket(): cannot bind main socket
(info) 17:58:29 void QtLanguage::loadLanguageFromConfig(): no Qt translation available for locale ''
(debug) 17:58:29 void QtLanguage::loadLanguageFromConfig():
(info) 17:58:29 void QtLanguage::loadLanguageFromConfig(): no application translation available for locale ''
Signal catched: SIGCHLD
QProcess: Destroyed while process is still running.

Fins aquí els missatges són els habituals.
La resta, que sembla indicar un error de connexió amb un proxy, probablement tingui a veure amb algun error de configuració dels paràmetres de connexió del propi programa.

---

### Post by lo gambusí on 2007-12-08
I què me recomanes que face?

---

