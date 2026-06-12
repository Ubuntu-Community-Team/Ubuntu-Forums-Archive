---
title: "Cool animated boot splash screen like Ubuntu Kylin"
date: 2014-09-25
forum: Desktop Environments
---

### Post by Sun.Dial on 2014-09-25
I accidentally downloaded and installed Ubuntu Kylin (for Chinese, I wasn't paying full attention to the download!) and was startled to see such a cool animated boot splash screen. How do you get it to work with UK Ubuntu instead of the sequential red dots?

---

### Post by Dennis N on 2014-09-25
It is most likely using a different Plymouth theme (used for booth splash) than Ubuntu uses. You can install a different one in Ubuntu if you want - these can be animated. Search for "plymouth-theme" in Ubuntu Software Center. Solar is probably the best one there. There are more and some better out on the web - see gnome-look.org - click on "splash screens" in the directory on the left of their first page. You have to install many of these manually, but it's not hard to do.

---

### Post by Sun.Dial on 2014-09-26
The original boot splash screen showed an impressive background of flashing stars, an animated multicoloured plasma cloud with 'Ubuntu Kylin' text superimposed. I installed Kylin on a victim machine and searched in the software centre for 'Plymouth' but it was unknown. However I did find it to be installed in my other PC running Ubuntu 14.04. Kylin has a program called 'youker-assistant' which looks like a combination of system tweaker/cleaner tools, including one to alter the boot animation. I tried this but was unimpressed by the result, and could not revert to the original.
Looking at the reviews of the Plymouth interactive interface did not give much confidence in using it, so I don't think I'll pursue it any further for the moment. Thanks for taking the time to reply.

---

### Post by Dennis N on 2014-09-26
You would have to search for "plymouth-theme", not just "plymouth". Then they will appear in the Software Center. If Kylin uses Plymouth for the boot splash (probably does if based on Ubuntu), the particular theme they use should be usable in standard Ubuntu. The themes are in /usr/share/plymouth/themes, so you can see what is already available on the system.

---

### Post by CantankRus on 2014-09-27
> **Sun.Dial said:**
> I accidentally downloaded and installed Ubuntu Kylin (for Chinese, I wasn't paying full attention to the download!) and was startled to see such a cool animated boot splash screen. How do you get it to work with UK Ubuntu instead of the sequential red dots?

Install the package ubuntukylin-theme.
```
sudo apt-get install ubuntukylin-theme
```

Change the default plymouth in alternatives.
Choose **ubuntukylin-logo.plymouth**
```
sudo update-alternatives --config default.plymouth
```

Then run...
```
sudo update-initramfs -u
```

ubuntukylin-theme includes an icon and gtk theme.
It also adds a background image for grub which will show after grub is updated.
```
sudo update-grub
```

If you don't want the background image, run
```
sudo rm /boot/grub/ubuntu_kylin_grub_bg.tga && sudo update-grub
```

---

### Post by Mike_Walsh on 2014-09-28
@Cantankrus;

When you say 'Change the default plymouth in Alternatives', where exactly IS 'Alternatives'?

I ask, because I thought I'd have a go at installing the 'Solar' theme, following yours and Dennis's info. I assume your method would also work for installing other themes?

I've installed 'Solar' via the Software Centre. I'm assuming it now needs to be set as default, so.....what would be the best way to proceed?

Regards,

Mike.

@Sun.Dial; apologies for hijacking the thread!

---

### Post by Dennis N on 2014-09-28
Since CantankRus is not around, I will take the liberty to answer: "Alternatives" is short for "Debian Alternatives" and is the system in which you choose the specific Plymouth theme to use. Google it for full information and a fun read.

Just run the two commands that he mentioned (and I neglected to mention):
```
sudo update-alternatives --config default.plymouth
```
in which you choose the new theme (solar) by number, then
```
sudo update-initramfs -u
```
to be sure it shows up as it should (we hope) when you boot.
Then reboot the computer. 

If you want to go back to the original theme, repeat and choose your original theme.

---

### Post by Mike_Walsh on 2014-09-28
Ah! THAT was the bit I didn't understand; that you choose from a list of themes by number.

Serves me right for jumping into the middle of somebody else's thread like that...!

Anyway; thanks once again for a nice, clear explanation, Dennis. You're rapidly becoming my 'go-to' man for this kinda stuff! I've run the commands through the terminal, and it's all working **nicely**; those solar flares are quite nifty. Makes a nice change to have something different to look at... ;)

Appreciated. I'm learning more and more about this thing every day; and I'm **loving **every minute of it. It's certainly a hell of a lot easier to make fundamental changes to theming and appearance than it **ever **was in XP...

Cheers!


Regards,

Mike.

---

