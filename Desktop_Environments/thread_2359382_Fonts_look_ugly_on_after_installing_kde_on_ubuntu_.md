---
title: "Fonts look ugly on after installing kde on ubuntu 16.04"
date: 2017-04-23
forum: Desktop Environments
---

### Post by termibuntu on 2017-04-23
Hello. I have recently installed kde alongside unity on my ubuntu laptop. But, after doing so, the fonts look extremely bad and on unity, the fonts are normal. I have tried everything with changing the theme, the font, the sub pixel rendering type and so on and so on etc. etc... But again, nothing helped. I have attached some screenshots of the bad font on kde, and also unity rendering fonts correctly. I really like kde but with this problem, its not the same. I have also tried modifying config files and also deleting them but nothing helps. The version of kde is 5.5.5 plasma. Thanks in advance and I hope that I can fix it. :(

---

### Post by SeijiSensei on 2017-04-23
On a pure KDE machine, you would control the fonts via System Settings > Application Appearance > Fonts.  I don't know if that's available on a machine where KDE is installed on top of Unity.  As a long-time KDE user, I only ever use Kubuntu.

---

### Post by termibuntu on 2017-04-23
I have already said that I have tried that, and it was available. The thing is, changing font does NOTHING, at all. And so, I need another solution to try. EDIT: is anyone here?

---

### Post by ajgreeny on 2017-04-23
I had a similar problem in Xubuntu after making changes using the KDE system-settings application.

I found that I needed to remove the file **~/.config/fontconfig/fonts.conf** which can cause rendering to become thin and spidery.  Remove it for proper gtk rendering.

If that does not help I am not sure what else to suggest.

---

### Post by termibuntu on 2017-04-23
Oh I'll try that. :) I think it must be configuration. And yes. In my screen shots, it DOES look fhin and spidery. If it works then great, I can continue using kde. Thanks for that (potential) solution. I'll get back when I've done it.

---

### Post by termibuntu on 2017-04-24
Hi. Nothing happend. I have deleted it but the font rendering remains the same. There were 2 fonts.conf : first in the place you said and second there is one in /etc/fonts. The first fonts.conf is in my home directory. But the second one is in /etc/fonts as I already said. If I can't do anything about, I won't be able to go on kde.

---

### Post by vasa1 on 2017-04-24
When I started using the [Openbox session of Lubuntu]("https://ubuntuforums.org/showthread.php?t=2173126&p=12787508#post12787508"), fonts didn't appear healthy. Then, I came across a link (which doesn't work anymore) but it suggested that I have a file called ~/.Xresources with this content:```
! Render setting for cairo -> pango -> gtk
Xft.dpi:        96
Xft.antialias:  true
Xft.hinting:    true
Xft.rgba:       rgb
Xft.hintstyle:  hintslight
```This was back in September 2013 and for Openbox and so I doubt very much it's relevant here but just in case it helps!```
xrdb ~/.Xresources
```will load that file for you in your current session. Otherwise, you can log out and log back in again.

---

### Post by SeijiSensei on 2017-04-24
> **termibuntu said:**
> If I can't do anything about, I won't be able to go on kde.
You'd be much better off installing Kubuntu if you want to transition to KDE.

---

### Post by termibuntu on 2017-04-24
But I don't want to install kde on its own. I'm still use and like unity, and don't want to leave it. Instead, I want to have two desktops. But the font problem happens everywhere, even where kde is on its own, in this case, kubuntu.

---

### Post by SeijiSensei on 2017-04-24
I use the [Microsoft font package]("https://www.ostechnix.com/install-microsoft-windows-fonts-ubuntu-16-04/") with Arial as my base font, and it looks fine.  I have this configuration on a number of machines.  Do you have the same problem across all fonts?

---

### Post by termibuntu on 2017-04-24
But will the Microsoft font package make it all normal? Is yes, how do I configure kde to use those fonts after being installed using the tutorial you have supplied? Microsoft windows fonts on ubuntu would look great. And on kde yes, I have the problem with all fonts. In Unity, all fonts are fine, look good and readable.

---

### Post by SeijiSensei on 2017-04-24
On a vanilla KDE setup, you'd use System Settings > Application Appearance > Fonts and choose Arial from the list.  I don't know how "System Settings" works in a hybrid environment like yours.

I recall not liking the default font that came packaged with Ubuntu which led me to using Arial.

---

### Post by termibuntu on 2017-04-25
Hmm, I do have both kde and unity settings. Both different settings control the corresponding desktop. I'll try changing font. Also Microsoft fonts would look great on kde. As I said they would..
EDIT: changing font to the Microsoft core fonts on arial did nothing. I still have the bad font.

---

### Post by termibuntu on 2017-04-25
I now have to reinstall ubuntu. The distribution upgrade froze. :( But at least my kde font problem will be solved. And now, I lost all my data. What can I do?

---

### Post by vasa1 on 2017-04-25
> **termibuntu said:**
> I now have to reinstall ubuntu. The distribution upgrade froze. :( But at least my kde font problem will be solved. And now, I lost all my data. What can I do?
Please start a new thread for data recovery. Thanks.

---

### Post by termibuntu on 2017-04-26
Also, while upgrading, I encountered an error that said my ubuntu installation is broken. That must be something to do with the problem with kde. Now I may have found out what has been causing these kde issues.

---

### Post by termibuntu on 2017-04-28
I have now reinstalled ubuntu and kde, My fonts are back to how they should have been. Although I didn't have much on my installation, all I had was lots of programs and nothing else. Thank you for your answers. I appreciate it.

---

