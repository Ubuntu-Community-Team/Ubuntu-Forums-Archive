---
title: "What's preventing me from using ubuntu"
date: 2006-08-01
forum: Desktop Environments
---

### Post by joshier on 2006-08-01
Hello

Firstly, I am very busy, and don't have much time (4 hours freetime a day, this includes eating time and so on after I come home from work)

Basically, I have mepis, windows xp and ubuntu.

Windows ruined grub instillation so I fixed it with mepis, but mepis didn't add a line for ubuntu.

I can add ubuntu to the grub .list file only if I know what exactly to put in there (if someone can tell me that would be great)

Second thing preventing me from using it... is the internet, as it will take a little time to install ndiswrapper (no biggie, I understand that my broadcom wifi is pants).

Third, I'd love to install automatix, but it seems the guys over there don't understand that some people would actually like to download automatix without going into ubuntu first (perhaps because they have no internet?) - Therefore, I need a proper URL to the actual package file (.deb?) .. I think I like .deb's because when I click them they open the synaptic package manager and they install... without me having to go into command line.

If these solutions are met, I'd be using ubuntu to post now :)


Thank you.

---

### Post by aysiu on 2006-08-01
Sounds like Mepis is your cup of tea. Worked for me as a first distro.

---

### Post by joshier on 2006-08-01
I don't care what mepis is doing.. ubuntu is supposed to be easy, and it will be easy if people prevail.

It's easy saying to stick with mepis, but I don't want to.

Why is ubuntu not so easy?.. well it needs work done, and I am just another person outlining the problems and giving solutions.

Anyway, on a different note, that was very off topic and not what I wanted to hear.

---

### Post by aysiu on 2006-08-01
Ubuntu was easy for me. I didn't experience the problems you did. Since it was difficult for you, you should consider sticking with Mepis. What's wrong with Mepis?

---

### Post by joshier on 2006-08-01
Mepis has decided that ndiswrapper isn't going to sort out my wifi drivers, therefore I'm trying ubuntu.

---

### Post by patrickthebold on 2006-08-02
Heres my ubuntu lines for grub:

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot

Clearly you will have to change the kerel version and the root device to match yours...both the (hd0,0) and the root=/dev/hda1... see [http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration](http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration)
for more help.

---

