---
title: "Gnome 3: could not list shell extensions"
date: 2011-11-07
forum: Desktop Environments
---

### Post by antoineb on 2011-11-07
Hi there,

I'm running Ubuntu 11.10, and I'm having problems getting the gnome shell extensions to work. I've installed them by following these steps:

sudo add-apt-repository ppa:ferramroberto/gnome3 
sudo apt-get update 
sudo apt-get install gnome-shell-extensions-common

However, when I open the Advanced Settings and go to the Shell Extensions tab, nothing is listed there. I have tried logging out and back in, even restarted my computer but that hasn't made any difference. I've also tried re-installing gnome-shell-extensions-common, but the terminal tells me that it's already installed...

I'm a bit lost there, can anyone help with this? I'm wondering if I missed something, I've reviewed many forum topics but haven't found any help with that yet :/

Thanks in advance!!

---

### Post by krack3rz on 2011-11-12
crap, double posted, can i delete?

---

### Post by krack3rz on 2011-11-12
Dude, me2...
I installed every extention, nothing works.

It'd be a good idea for us to list some specs so that we may match and find different ways we did whatever, it could help.


Some Specs.:
Unity (not 2d), Ubuntu Oneiric 11.10 32-bit, cairo-dock

installed every extention, added PPA for it all, got gnome-tweak-tool installed, got gconf installed

Ofc, latest updates

thats it so far

---

### Post by Bobhuber on 2011-11-12
> **krack3rz said:**
> Dude, me2...
I installed every extention, nothing works.

It'd be a good idea for us to list some specs so that we may match and find different ways we did whatever, it could help.


Some Specs.:
Unity (not 2d), Ubuntu Oneiric 11.10 32-bit, cairo-dock

installed every extention, added PPA for it all, got gnome-tweak-tool installed, got gconf installed

Ofc, latest updates

thats it so far
[http://askubuntu.com/questions/75530/how-to-install-gnome-shell-extension](http://askubuntu.com/questions/75530/how-to-install-gnome-shell-extension)

---

### Post by krack3rz on 2011-11-13
Yea so when I installed the extensions and stuff, I did it exactly like that, except I got it from: [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html]("http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html")

And I still have the problem described above, so, no cigar...

---

### Post by Lateralus138 on 2012-02-29
I have this same problem.... any solutions?

---

### Post by apple_head on 2012-03-23
I am having this problem too?

I have an ATI card installed with the additional proprietary driver installed?

---

### Post by Bobhuber on 2012-03-23
You need to use web8 for everything and make sure the other repository is removed along with the software it installed. Also note that NONE of the extensions work with the still in development 3.3. Make sure your installing 3.2 stuff.
After installing the packages you need to go into synaptic or the software center and select the ones you want to install and activate them in the tweak tool.

---

