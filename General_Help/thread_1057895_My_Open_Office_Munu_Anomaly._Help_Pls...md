---
title: "My Open Office Munu Anomaly. Help Pls.."
date: 2009-02-02
forum: General Help
---

### Post by sayabis on 2009-02-02
I'm having problems with my menus in all my open office apps including scribus. I can't seem to see the "text" in the menus. But my other apps like gimp, inkscape, games, firefox, etc are all working fine. I think it's a graphic problem. I tried turning off desktop effects but still can't determin the anomaly. Any help will be very much appreciated.

Attached are the Screen shots. You will see that the "text" in the menus can't be seen. Only the underscores are visible. Is there a solution for this?

---

### Post by AliTabuger7 on 2009-02-02
I've never seen this error before, but until someone who has comes along, I would suggest that you try changing the default font using the system>preferences.

If its graphical, you can sometimes "shake it off" by maximizing, minimizing, and resizing the window.

---

### Post by sayabis on 2009-02-02
Yes it's very wierd. I tried to shake it off like you said by minimizing and maximizing. Still no improvements. All other apps looks fine except for open office and scribus. Compiz effects are working flawlessly. The only thing I could think of is to turn compiz off. Jeez, This is annoying!

(A few minutes later)

I turned the desktop effects completely off and now open office menus are working fine. I turned my Ubuntu back to its boring setup. Zero effects. Arrrrg!

---

### Post by AliTabuger7 on 2009-02-02
You mention scribus too?

Are there any other programs that do this... i'm looking for some kind of pattern...

Inkscape? GIMP?

If its a graphical issue, theres a weird configuration thing that I read once that MAY have to do with this. Its a font configuration you put in xorg.conf .

---

### Post by sayabis on 2009-02-02
> **AliTabuger7 said:**
> You mention scribus too?

Are there any other programs that do this... i'm looking for some kind of pattern...

Inkscape? GIMP?

If its a graphical issue, theres a weird configuration thing that I read once that MAY have to do with this. Its a font configuration you put in xorg.conf .

Inkscape and Gimp text menus are ok. Only open office apps and scribus are affected.

---

### Post by IceReaver75 on 2009-02-02
if your using a nvidia card thats what is causing it.  I had the same problem with my card which is a nvidia 6200.  Every driver i used that is listed in the hardware list did this.  I had manually install the 180.22 driver from the nvidia site and it took all the problems away.

---

### Post by sayabis on 2009-02-02
> **IceReaver75 said:**
> if your using a nvidia card thats what is causing it.  I had the same problem with my card which is a nvidia 6200.  Every driver i used that is listed in the hardware list did this.  I had manually install the 180.22 driver from the nvidia site and it took all the problems away.

yep i'm using an old nvidia mx4000 card. Actually I was surprised that my old card was able to use the compiz desktops effects, but only to find out later it had problems with the Open office menus. LOL.

I'll try installing manually the updated drivers 2morrow. I'm still learning the ways of linux (I'm still new to the linux environment). I'm sure I'm gonna need to recompile the new nvidia drivers to install. :-(

---

### Post by IceReaver75 on 2009-02-02
you will want to use this driver which is the updated legacy drivers for the geforce 2-4 series cards.  The 180.22 driver is for geforce 6series and higher

[http://www.nvnews.net/vbulletin/showthread.php?t=116407](http://www.nvnews.net/vbulletin/showthread.php?t=116407)

---

### Post by sayabis on 2009-02-02
> **IceReaver75 said:**
> you will want to use this driver which is the updated legacy drivers for the geforce 2-4 series cards.  The 180.22 driver is for geforce 6series and higher

[http://www.nvnews.net/vbulletin/showthread.php?t=116407](http://www.nvnews.net/vbulletin/showthread.php?t=116407)

I will try that. tnx for help. :-)

---

### Post by sayabis on 2009-02-03
I'm having problems installing the legacy drive 96.43.07 of Nvidia for the MX4 Series.

I'm getting this error: "Unable to build nvidia kernel module"

The steps I made:
1. ctrl + alt + f1 
2. logged in
3. typed "sudo Killall gdm"
4. sudo /etc/init.d.gdm status (to see if gdm is not running)
5. typed "su" to log as root
6. cd Desktop (location of the NVIDIA driver)
7. typed "sh NVIDIA-Linux-86-96.43.07-pkg1.run"
8. Followed all the instructions to compile kernel

After that I got the error: "Unable to complie NVIDIA kernel module".

Bummer!

---

### Post by IceReaver75 on 2009-02-03
try installing the linux-source-2.6.27 package through synaptic.  I was getting the same problem until I installed that package.  after the package install the nvidia kernel installed with no problems.

the steps I took to install my driver where 

ctrl-alt-f1
sudo /etc/init.d/gdm stop
sudo sh Nvida driver name
then after the install completed
sudo /etc/init.d/gdm start

---

