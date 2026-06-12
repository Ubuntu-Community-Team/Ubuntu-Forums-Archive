---
title: "Firefox crashes silently (error logs included)"
date: 2005-11-18
forum: Desktop Environments
---

### Post by matheus on 2005-11-18
I am using Ubuntu for a week or so and everything was fine. I believe the problem I will describe here started to happen after I installed some packages and updates, but since the problem only occurs at certain sites, I am not really sure.

The fact is that Firefox silently crashes when I click certain links. I can reproduce this behavior every time. I tried complete removal and reinstallation with no luck. The Javascript console shows a cryptic error message (below»):

```

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

```

Actually, there are lots of messagens identical to the above in the console, but only sometimes will the browser actually crash.

Any help is appreciated

---

### Post by ThirdWorld on 2005-11-18
i dont know if this will help but there is an extension called session saver it will save all your open browsers so if firefox crash all you have to do is restart firefox and it will open all those websites again for you. go to the firefox webpage and search for extensions.

---

### Post by matheus on 2005-11-18
Thats a good one I will take a look

Thanks

---

### Post by Efwis on 2005-11-18
what java package are you using???? blackdown or did you download Sun's Java?

---

### Post by matheus on 2005-11-18
I did install Java 1.5 from Sun, as a Debian package. I also remember following some instructions yestarday on the Ubuntu wiki to set this as the default JVM (it was using the dpkg command). However I don't know how for sure which JVM Firefox is using.

Does this help?

---

### Post by Efwis on 2005-11-18
[QUOTE=matheus]I did install Java 1.5 from Sun, as a Debian package. I also remember following some instructions yestarday on the Ubuntu wiki to set this as the default JVM (it was using the dpkg command). However I don't know how for sure which JVM Firefox is using.

Does this help?[/QUOTE]
open a new tab in FF and type the following:
```
about:config
```
in the filter bar that opens with that command type in **java**

the line you are looking for is **java.global_java_version_file**

what is that value pointing to. in mine it's **/etc/.java/versions**
Also could you post a link to the site your are going to so that I can see if it does it to mine also. thsi way we can determine whether or not it's the site or your system.

---

### Post by matheus on 2005-11-18
I did what you said and it shows /etc/.java/versions too.

I also discovered how I reconfigured te default JVM, it was using "sudo update-alternatives --config java". Here are the ones I have installed:

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java
 +    4        /usr/lib/j2se/1.4/bin/java

Now for the link, I'd have posted it in first place but it is inside a corporate webmail... actually I wouldn't care for it if it was not at THAT place :)

---

### Post by Efwis on 2005-11-18
fair enough about the webmail issue. completely understandable :)

I think we might have found the problem. Here is my config display.

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/local/jdk1.5.0_05/bin/java

it appears that it is trying to user the 1.4 on your system along with 1.50. unless you have to have it, I would recommend getting rid of the 1.4 instance. looks like that is the blackdown version. regardless you can use synaptic to get rid of it. 

run synaptic then click on the button that says **status** then click on installed and scroll down to find the java 1.4 installation. righ tclick and choose complete removal. 

it also looks like you didn't install sun java 1.50 correctly. there .deb release doesn't work proplerly with ubuntu because of the way they encoded it. I would recommend uninstalling it and reinstalling it using the directions on the wiki here [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)
scroll down and follow the instructions for installing sun java.

after you have done that, try that website again and let us know if it works.

---

