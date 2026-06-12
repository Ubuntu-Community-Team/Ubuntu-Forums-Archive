---
title: "How do I install Flash and Java on Linuc, I am so lost."
date: 2009-05-24
forum: General Help
---

### Post by Mashuteichou on 2009-05-24
I have tried everything under the sun to install it.  But I fail.  When I load Firefox and go to a flash related site like Youtube, all it shows is a black box with a play button.  When I hit the button, nothing happens.   I resorted into loading Firefox and Flashplayer for windows, just so I can use the flash player.  Same goes with Java.  I can't figure it out.  I feel like such a noob.   D:

---

### Post by oldos2er on 2009-05-24
Have you tried running
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```
in a terminal?

---

### Post by Mashuteichou on 2009-05-24
Yep, I loaded that when I first loaded Ubuntu.  ^_^   But it doesn't work.  Firefox in Linux doesn't want to run Flash player or Java related stuff.  I get flash stuff to work in other browsers, but not Firefox.  But as far as java, I have no idea how to do that yet.

---

### Post by oldos2er on 2009-05-25
Have you installed gnash or any other flash player? You may need to uninstall them, then try reinstalling flash.

 ubuntu-restricted-extras used to contain some Java, I don't know if that's no longer the case. But you could try
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
 When the EULA comes up, hit 'Tab' to highlight 'ok,' then press Enter.

---

### Post by Mashuteichou on 2009-05-26
Yeah, I installed Swfdec flash player and Gnash.  I also have the open java and java 6 downloaded and installed.  But, for some reason, my firefox refuses to work.  

Now the funny part is, for some reason, Youtube works fine now, but other flash sites down.  Even other video sites.  It just comes up with a play button, and nothing happens when I hit it or let it go.  

And I tried the terminal command, but it just came up with an error.

---

### Post by oldos2er on 2009-05-26
Can you copy and paste the error here?

---

### Post by Mashuteichou on 2009-05-26
Actually I didn't get an error this time.  I just said nothing was changed basically.  

And here is what I get for a flash page:  

You are trying to install Adobe Flash Player on an unsupported operating system.  For system requirements, please visit: Flash Player System Requirements.  (link)  

for Flash Player, please visit:  Flash Player Download Center (link)

---

### Post by Mashuteichou on 2009-05-26
And I just realized I mispelled "Linux".  I always hit C instead of X.  Its so annoying.  >_<

---

### Post by zobcat on 2009-05-26
you need to uninstall swfdec and gnash and reinstall adobe-flashplugin.

```
sudo aptitude remove gnash swfdec-mozilla swfdec-gnome
```

```
sudo aptitude reinstall adobe-flashplugin
```

---

### Post by xXeHPiCXx on 2009-05-26
Have you looked in add&remove or synaptic?I installed it from the java site.They detect that your using ubuntu.All you have to do is select what kind of package like debian.

---

