---
title: "No GMenu on Kiba Dock"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by Ebuntor on 2007-09-26
Hi everyone,

GMenu isn't showing on my Kiba dock.  It appears in the settings (and the config file) and I have it enabled. I first installed it via Treviño&#8217;s repository. After that I removed it and compiled it from the svn sources, I used [this howto]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba"), however it still doesn't show up.

Any ideas?

Thanks in advance :)

EDIT: Seem that[ someone else has the same problem]("http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=485.msg%25msg_id%25") but compiling it did fix it for him. I did exactly the same things as he did.

---

### Post by Ebuntor on 2007-09-27
*bump*

---

### Post by Ebuntor on 2007-09-27
*bump again*

Can anyone help me, please?

---

### Post by Ebuntor on 2007-09-28
*bump* one more try

---

### Post by duncan.hawthorne on 2007-10-02
when you compile the kiba-plugins package, does it say gmenu compiles correctly?

the trevino repository has been updated recently and has almost everything that compiling directly from svn does.. (svn has recently got parabolic zoom which is very cool, however). If you use trevino and install kiba-plugins and kiba-plugins-gnome the gmenu should work.

hope it helps

---

### Post by Mayfairy on 2007-10-02
Brilliant! Installing kiba-plugins and kiba-plugins-gnome did work for me. I had disabled kiba-dock repository earlier because I'm a bit paranoid of those Compiz/Emerald updates. Not all of them have worked for me and finally I found version that works nicely for me. 
Too bad it's only GMenu. It's nice alright, but USP would have been something totally different.

---

### Post by deigote on 2007-10-17
Hi! Look carefully at autogen output in kibadock-plugins. Its list the plugins that will be compiled and not, and with the not-compiled ones, the reason for not compiling.

For example, I didn't get gmenu because I needed to install libgnome-menu-dev.

---

