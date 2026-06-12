---
title: "Menus after installing KDE on Ubuntu"
date: 2006-01-06
forum: General Help
---

### Post by mark52230 on 2006-01-06
Hi,

I've just installed KDE (not the Kubuntu desktop) on my Ubuntu install.. In my KDE menus I can see Gnome applications and in Gnome I can see KDE applications.. Can I separate them so I only see Gnome applications in Gnome and only KDE applications in KDE?

Thanks!

---

### Post by snowjunkie on 2006-01-06
I believe KDE and GNOME share the same menu settings, so I'm not sure you can separate them!  I could well be wrong...

---

### Post by mark52230 on 2006-01-06
Ok then is it in any way possible to install default kde stuff?

If I install Ubuntu and then install kde, then I get all the stuff from the default kde packages (kdemultimedia, kdeartwork, etc etc) but then I've got a load of applications that I don't want that came with Gnome..

If I install Kubuntu then it doesn't install the default kde stuff but a "customised kde" without things like kdemultimedia but with extra kde applications in their own packages.. So if I then install the default kde on Kubuntu I'm left with two media players or two IRC clients, one is from the Kubuntu install and one is from the default kde setup.. I only want the applications that come with KDE by default, not these extra ones that Kubuntu comes with..

Hope that makes sense!

---

### Post by everettattebury on 2006-01-27
[QUOTE=mark52230]Hi,

I've just installed KDE (not the Kubuntu desktop) on my Ubuntu install.. In my KDE menus I can see Gnome applications and in Gnome I can see KDE applications.. Can I separate them so I only see Gnome applications in Gnome and only KDE applications in KDE?

Thanks![/QUOTE]


I found the following here: [http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/")

> 
So you have Ubuntu installed and want to try out Kubuntu instead?

Easily Done!

Install the “kubuntu-desktop” meta-package, and you will have the option to log in to a KDE session the next time you boot up (Choose KDE from among the session options, before you enter the username and password in the graphical login screen)

You can install kubuntu-desktop by seraching for it in Synaptic, or simpler still, using the command:
$sudo apt-get install kubuntu-desktop

kubuntu-desktop is an architected collection of carefully selected KDE applications that creates a unique “desktop” experience, much like Ubuntu - it has one software utility for each function, again, like Ubuntu. So installing kubuntu-desktop will not give you all the KDE utilities, just like installing Ubuntu did not give you all the Gnome applications. There is another meta-package called “KDE” which, when installed will give you a different set of software. So if, after installing kubuntu-desktop, you find some of your favorite KDE apps missing, install the entire KDE suite, by installing the kde metapackage. I find this unneccassary, as kubuntu-desktop provides me with the minimal set of tools to get my work done. If I need something extra, like, kile, that very useful LaTeX editor, then I just install kile. Less baggage, better trip!

If you already knew all that was written above, and are beginning to think that it was a waste of time reading so far, fear not! I have a tip (not my original idea) that will make it worth your time.

The biggest annoyance for me, with having both gnome and KDE installed is that some KDE apps show up in the Gnome menus and some Gnome apps show up in the KDE menus. While this is not a “bad” thing, I would rather do without this.

To prevent KDE apps from showing up in Gnome menus and vice-versa, do the following before you install kubuntu-desktop :

(you can also create a small cleaner.sh script witht he following and run it as root)
$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo ‘OnlyShowIn=GNOME;’ >> $i \
# fi
#done

Now, after installing kubuntu-desktop do:

$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo ‘OnlyShowIn=KDE;’ >> $i
# fi
#done

What we did above was to tell the Gnome apps to only show in the gnome menus, and later, the KDE apps to only show in KDE menus. 

---

### Post by s_spiff on 2006-01-28
I would reccomend this : [http://www.ubuntuforums.org/showthread.php?t=114158&highlight=Keeping+GNOME](http://www.ubuntuforums.org/showthread.php?t=114158&highlight=Keeping+GNOME)
I got a way to clear the GNOME of all the KDE menus, now have to find one for clearing KDE of all GNOME app's... dang.

---

### Post by s_spiff on 2006-01-28
ohh I see now someone's posted how to clear KDE menu's too. Cool.

---

### Post by tariqf on 2006-01-28
Hi sorry for being thick but I cannot work out how to get you instructions to work!

How do I create the cleaner.sh script? If I create it containing what you have said 

for i in *.desktop; do \
 if ! grep -q ^OnlyShowIn= $i; then \
 echo ‘OnlyShowIn=GNOME;’ >> $i \
 fi
done


- I get syntax errors. Please can you clarify what cleaner.sh should contain?

---

### Post by RaiSuli on 2006-02-06
I'm trying to do the same thing, but can't get it to work. Can the commands just be entered into the terminal?

---

### Post by everettattebury on 2006-02-06
I'm really not that familiar with shell scripts yet, sorry.  I just posted the info that I happened to find elsewhere, and after trying it,I had the same problems with it that you did.  Maybe someone with a better understanding can look at the scripts and see what is wrong with the syntax.  Next time I will try it out BEFORE I post. 

I ended up installing the .deb's I found [here]("http://www.kde-look.org/content/show.php?content=31031") and [here]("http://gnome-look.org/content/show.php?content=31035"), and they seem to be doing the job pretty well.

---

### Post by lewisskinner on 2008-02-20
> **everettattebury said:**
> I found the following here: [http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/")

this doesn't work :(

---

