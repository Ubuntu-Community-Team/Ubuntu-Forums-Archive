---
title: "Installing JRE and Mozilla Plugin"
date: 2009-04-05
forum: General Help
---

### Post by JasonDFR on 2009-04-05
I'm getting this error when attempting to connect to WebEx with FireFox:

 	
"Meeting Center cannot be installed because Java is disabled in your Web browser. Please enable Java in your browser, and then click Set Up again. For instructions on enabling Java, refer to your browser's online help.

If Java cannot be enabled for any reason, you can download the manual installer and install it from your desktop by double-clicking the installer icon."

I need to install the JRE and mozilla plugin.

Google returned a lot of outdated information and I want to be sure I am doing this correctly.

Synaptic has sun java jre and sun java plugin. It also has openjdk. I need a jre and plugin.

What should I install?

Thanks!

---

### Post by taurus on 2009-04-05
Install sun-java6-bin, sun-java6-jre, & sun-java6-plugin.

---

### Post by JasonDFR on 2009-04-05
Thanks for the reply, I've done it.

I no longer get the same error, however, I don't successfully connect to the webex test either. Try it here:  [http://developers.webex.com/api/jointest/index.php](http://developers.webex.com/api/jointest/index.php)

I found this at [http://www.gargolito.com/2008/11/how-to-fix-webex-in-ubuntu-hardyibix.html](http://www.gargolito.com/2008/11/how-to-fix-webex-in-ubuntu-hardyibix.html) :

1. sudo apt-get install libstdc++5 sun-java6-plugin
2. Edit your ~/.profile and add these two lines:
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.66
export PATH=$JAVA_HOME/bin:$PATH
3. Restart X by logging off/on or ctrl+alt+backspace

Is this the best advice?

Thanks

---

### Post by JasonDFR on 2009-04-05
I did this:

1. sudo apt-get install libstdc++5 sun-java6-plugin
2. Edit your ~/.profile and add these two lines:
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.66
export PATH=$JAVA_HOME/bin:$PATH

And it worked. I still have two questions:

Should /usr/lib/jvm/java-6-sun-1.6.0.66 in the above be 1.6.0.13 as that is the version installed on my machine.

And secondly, how does anyone know that this needs to be done in the first place?

Thanks as always.

---

### Post by moataz_mmdh on 2009-10-04
it does not work with me

Ubuntu 9.0.4

---

