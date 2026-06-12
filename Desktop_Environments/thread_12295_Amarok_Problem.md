---
title: "Amarok Problem"
date: 2005-01-23
forum: Desktop Environments
---

### Post by redman5087 on 2005-01-23
I tried to install AmaroK by synaptic but this fails.
However, I successfully installed it from source!
I modified the file types so that AmaroK is used!
So when I double-click on a mp3 file AmaroK is opened and playing the file!
But when I click on another file, I want that AmaroK uses the one that is open and not  open another window of AmaroK.
You can feed AmaroK with commands to , for example, stop playing or pause but when I do that It opens another window of Amarok.
How do I fix this problem so that only one instance of AmaroK can be open?

Kind Regards
Redman

---

### Post by redman5087 on 2005-01-24
little help, please

---

### Post by martijntje on 2005-01-25
[http://amarok.kde.org/component/option,com_staticxt/staticfile,cmd-line-options.html](http://amarok.kde.org/component/option,com_staticxt/staticfile,cmd-line-options.html)

---

### Post by redman5087 on 2005-01-26
[QUOTE=martijntje][http://amarok.kde.org/component/option,com_staticxt/staticfile,cmd-line-options.html](http://amarok.kde.org/component/option,com_staticxt/staticfile,cmd-line-options.html)[/QUOTE]

I know the commands but they don't work with the amaroK window that is open but instead it opens I new window of amaroK!!

Redman

---

### Post by Ironi on 2005-01-27
> 
  I tried to install AmaroK by synaptic but this fails.
  
 How so? There was a conflict problem a week ago or so in Hoary, but AFAICT that's been cleared up. At least, amarok installed and (after that issue cleared up) upgraded fine for me.
  
  > 
  However, I successfully installed it from source!
  
  With e.g. "apt-get build-dep amarok; apt-get source -b amarok", or did you build from a tarball?
  
  > 
   I modified the file types so that AmaroK is used!
  
 Are you using GNOME or KDE? What command did you add? This stuff is usually handled automatically when you install the package...
  
  > 
   So when I double-click on a mp3 file AmaroK is opened and playing the file!
   But when I click on another file, I want that AmaroK uses the one that is open and not  open another window of AmaroK.
 You can feed AmaroK with commands to , for example, stop playing or pause but when I do that It opens another window of Amarok.
   How do I fix this problem so that only one instance of AmaroK can be open?
  
 I'm not sure... amarok 1:1.2beta3-0ubuntu1 doesn't even let me start multiple instances; running "amarok file.mp3" just empties the current playlist (but not the collection list), adds that file, and starts playing it.
  
  Anyways, try one of these for the association command (assuming that you're using KDE):
  
  amarok %U
  /bin/sh -c "dcop amarok player playMedia %U"

---

### Post by redman5087 on 2005-02-09
[QUOTE=Ironi]How so? There was a conflict problem a week ago or so in Hoary, but AFAICT that's been cleared up. At least, amarok installed and (after that issue cleared up) upgraded fine for me.
  
  
  With e.g. "apt-get build-dep amarok; apt-get source -b amarok", or did you build from a tarball?
  
  
 Are you using GNOME or KDE? What command did you add? This stuff is usually handled automatically when you install the package...
  
  
 I'm not sure... amarok 1:1.2beta3-0ubuntu1 doesn't even let me start multiple instances; running "amarok file.mp3" just empties the current playlist (but not the collection list), adds that file, and starts playing it.
  
  Anyways, try one of these for the association command (assuming that you're using KDE):
  
  amarok %U
  /bin/sh -c "dcop amarok player playMedia %U"[/QUOTE]



I'm not using KDE but GNOME
Installing by synaptic or apt-get doesn't work. It say it's missing components, if I select the sub components it complains about the main component and it goes on and on.


It' strange because I installed xine and it has the same problem too!


And 'amarok' '%U' doesn't help.

Thanx
Redman

---

### Post by Ironi on 2005-02-09
[QUOTE=redman5087]I'm not using KDE but GNOME
 [/QUOTE]
 Okay. I just tried the aforementioned version of amarok under GNOME -- no problems here (**amarok file.mp3** uses the already-running instance).
 
 > 
Installing by synaptic or apt-get doesn't work. It say it's missing components, if I select the sub components it complains about the main component and it goes on and on.
 
 Are you using warty? Try to install amarok and all of the missing components at once (e.g. **apt-get install amarok amarok-gstreamer ...**). If that doesn't work, it might be a dependency problem that still isn't fixed, or some missing package(s).
 
 > 
 And 'amarok' '%U' doesn't help.
 
 It wouldn't -- %U is what KDE's file association system uses for specified arguments... For nautilus, try this:
 [Right click on audio file] -> Properties -> Open With -> Add -> 
 Use a custom command -> amarok -> [Select amarok]
 
 It appears that that must be done for each audio file type as well. That works for me, playing a clicked file with the existing instance of amarok. If it doesn't for you, oh well... I give up. :p

---

### Post by redman5087 on 2005-02-16
Got things working now, my respository from hoary was not correctly configured.

Redman

---

