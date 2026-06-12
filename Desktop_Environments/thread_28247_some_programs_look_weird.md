---
title: "some programs look weird"
date: 2005-04-19
forum: Desktop Environments
---

### Post by Pulka on 2005-04-19
Hi!

I'm having a few problems with the looks of some programs. Most of them are fine, firefox, Thunderbird, synaptic, etc. But Xmule and OpenOffice are terrible. I can hardly read the letters. It seems that the fonts are disappearing. Does anyone has idea of what this is?

---

### Post by bored2k on 2005-04-19
Ditch xmule and try [http://www.amule.org/files/details.php?file=59](http://www.amule.org/files/details.php?file=59) , wich is pretty new amule for debian based distributions.

---

### Post by shakin on 2005-04-19
[QUOTE=Pulka]Hi!

I'm having a few problems with the looks of some programs. Most of them are fine, firefox, Thunderbird, synaptic, etc. But Xmule and OpenOffice are terrible. I can hardly read the letters. It seems that the fonts are disappearing. Does anyone has idea of what this is?[/QUOTE]

Have a look in the tips and tricks forum. There are a few how-tos about how to improve how your fonts work. Try one of those how-tos and see if the problem goes away. At least one of the how-tos will help you install true type fonts. I recommend doing that.

---

### Post by bored2k on 2005-04-19
Create a file with the name
.fonts.conf with this inside:
> <?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

Then place it in your /home/username directory and log out/log in and see the differences.

You can also check [http://ubuntuforums.org/showthread.php?t=23426&highlight=cleartype](http://ubuntuforums.org/showthread.php?t=23426&highlight=cleartype) if you like that one better.

---

### Post by Pulka on 2005-04-19
I already tried aMule, but i had problems connecting to server. With xMule i stopped having those problems. But even so, i had the same problem with aMule.

I have truetype fonts installed. 

The .fonts.config made things a little better, but it still looks funny.

Let me explain a little better. All the other programs are fine. I have truetype fonts in them, and i can use them. Its just openoffice and xMule (amule also). In openoffice i have the fonts installed also, but the looks are awfull

---

