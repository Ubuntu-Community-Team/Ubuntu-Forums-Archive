---
title: "Gtk-WARNING **: Unable to locate theme engine in module_path: &quot;ubuntulooks&quot;"
date: 2009-04-02
forum: General Help
---

### Post by Nixie Pixel on 2009-04-02
Hi, I've searched for the error message above and found it in various threads, but none of them seem to address this error directly.  I understand it has to do with running a custom theme (in this case I simply downloaded and installed the Slickness Black theme from gnome-looks), but I can't find any place that tells me how to fix this error.

It seems to send me this warning no matter what I do in the terminal.  Can anyone tell me what I need to do to fix it?

Thanks!

---

### Post by fballem on 2009-04-02
Many themes will specify not only a background, but also a specific set of icons, which are also themed.

Two things that I'd like to suggest. Try the first one and see if that corrects the problem. If the problem persists, then try the second one.

1) I had a quick look at the page for slickness-black and I'm wondering if you installed the suggested icons: [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)


2) I'm not sure what version of ubuntu you are running, but ubuntulooks is a slightly older set of themes that aren't installed by default. Some themes don't provide all of the icons, but are dependent on the icons provided by a 'base theme'. If you open Synaptic (System > Administration > Synaptic Package Manager), and do a search for ubuntulooks, then an application called gtk-engines-ubuntulooks should be displayed. On my system, it is not installed. If it's not installed on yours, then right-click on gtk-engines-ubuntulooks, and mark it for install. There will probably be dependent packages to be included, which you should allow. When you select the Apply button, ubuntulooks will be installed.

I ran into the issue when I moved from 8.04 (where ubuntulooks was installed by default) to 8.10 (where ubuntulooks was not installed by default). At the time, I was using the blubuntu theme, which also depended on ubuntulooks.

Hope this helps,

---

### Post by Nixie Pixel on 2009-04-03
I installed the missing package.  Sorry about that, I should have done a package search, I feel silly.

---

### Post by Arup on 2009-04-03
In current stage, installing Uubntulooks would remove ubuntu human theme and ubuntu desktop due to a bug in the Human theme package. Add this repository and update Human theme and then install Ubuntulooks, that way you won't loose Human theme or ubuntu-desktop


Add Emilio's repository by adding "deb [http://ppa.launchpad.net/turl/ubuntu](http://ppa.launchpad.net/turl/ubuntu) intrepid main" and do a update check, you will be informed that Human theme needs to be updated, let it and then install ubuntulooks from synaptic of via apt-get.

---

### Post by fballem on 2009-04-04
> **Arup said:**
> In current stage, installing Uubntulooks would remove ubuntu human theme and ubuntu desktop due to a bug in the Human theme package. Add this repository and update Human theme and then install Ubuntulooks, that way you won't loose Human theme or ubuntu-desktop


Add Emilio's repository by adding "deb [http://ppa.launchpad.net/turl/ubuntu](http://ppa.launchpad.net/turl/ubuntu) intrepid main" and do a update check, you will be informed that Human theme needs to be updated, let it and then install ubuntulooks from synaptic of via apt-get.

What are the instructions if we're running Jaunty beta?

Thanks,

---

### Post by pjizz on 2009-06-01
> **fballem said:**
> What are the instructions if we're running Jaunty beta?

Thanks,

if you go to the index

[http://ppa.launchpad.net/turl/ubuntu/dists/](http://ppa.launchpad.net/turl/ubuntu/dists/)

you can see that he has the appropriate files for jaunty.  just change the deb line from 'intrepid' to 'jaunty'

---

### Post by Caseyjp on 2009-07-14
Just a quick thanks as well.  the PPA solved my issue with the most excellent "Orange-LinstaBlackPlastic" theme.  Also commented to the bug that this applies to to have this conflict permanently fixed for human.

---

### Post by LucianoP on 2010-05-05
I have just updated to Lucid Lynx 10.04 and now I am getting this error, however nothing shows up in Synaptic. I also tried "sudo apt-get install gtk2-engines-ubuntulooks" with no lucky.
Any guess?
Thx.

---

### Post by Runaway1956 on 2010-05-17
LucianoP - I've run into the same thing.  I upgraded using the alternate install CD, and was using the Slick Black theme in Intrepid.  Ubuntulooks just isn't available in Lucid yet.  I've searched and searched.

I have thought about using one of the repositories, and tell Synaptic to use the Intrepid repository, but, reading seems to indicate that might break other things. 

The desktop actually looks pretty good without ubuntulooks - and it works.  I may just leave it alone until someone sticks the ubuntulooks theme engine into a Lucid repository.

It's frustrating when you don't really understand all the consequences of tampering with things.  Oh well - crap happens.  I might change my theme to something that doesn't depend on ubuntulooks, but a LOT of popular, good looking dark themes seem to use it.

---

### Post by Stray Wolf on 2010-11-24
I'm bumping this since I have the same problem.  It's causing UCK not to work, and maybe causing other things to open a little slower or glitch.  Has anyone submitted this to Launchpad?

---

### Post by cybuntu on 2011-08-06
> **Nixie Pixel said:**
> I installed the missing package.  Sorry about that, I should have done a package search, I feel silly.

in that case, can you tell me how to install ubuntulooks :confused:
kthnxbai

---

### Post by iainmcc on 2011-10-16
I am getting a similar error on a fresh install of 11.10 with gvim and other apps. Here's my error message:


(gvim:16493): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (gvim:16497): WARNING **: Unable to register window with path '/com/canonical/menu/4200003': Timeout was reached

The second warning happens a while after gvim starts, and causes the window to glitch.

I'm going to put this up at launchpad -- a clean install from the ISO provided by Canonical should not have problems like this.

---

### Post by disasm on 2012-02-21
I know this is an old thread, but just came across the gvim pixmap issue. This was resolved by installing gtk2-engines-pixbuf. Just wanted to share the knowledge in case you never figured this out.

Sam

---

