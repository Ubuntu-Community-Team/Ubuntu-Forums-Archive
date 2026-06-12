---
title: "Installing GnomeBaker"
date: 2005-02-25
forum: Desktop Environments
---

### Post by ions on 2005-02-25
I did serach for this but came up empty handed.  I'm sure directions exist but I couldn't find them.  Other than 'Installing Gnomebaker' I didn't know what search terms to use.  So if this is a multiple post sorry, just point me in the direction of the original(s). :)

I need to burn a couple audio discs and would like to install Gnomebaker.  I know there is a Ubuntu package available for it here: [http://people.debian.org/~goedson/packages/ubuntu/warty/](http://people.debian.org/~goedson/packages/ubuntu/warty/)

How do I install this with apt?

---

### Post by landotter on 2005-02-25
To install "loose" .deb packages, at the command-line:

sudo dpkg -i nameofpackage.deb

You'll probably see some complaints about missing dependencies--use synaptic to grab those.

I'm using both Bnomebaker and Graveman successfully with Warty.

I couldn't find a warty .deb for Graveman so I installed the Mandrake cooker .rpm from rpm.find.net using "sudo alien -i package.rpm"

Alien is a tool to install non-native packages--use with caution of course. ;)

---

### Post by ions on 2005-02-25
Cool, it's installed.  Thanks! :)

And not a bad little app.  I'll need to spend some more time with it before I decide whether I like it better than Graveman or not.

---

