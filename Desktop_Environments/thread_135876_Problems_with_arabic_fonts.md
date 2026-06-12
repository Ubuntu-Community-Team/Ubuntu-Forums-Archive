---
title: "Problems with arabic fonts"
date: 2006-02-24
forum: Desktop Environments
---

### Post by tzopilotl on 2006-02-24
Hi people, I've just installed Ubuntu 5.10 in my computer.

The problem I have is very simple: Firefox uses a terrible font to show Arabic and Persian characters in the navigator screen. I tried switching to another font for the Unicode UTF-8 encoding, but the font remains the same, even after changing it. 

I have no idea how can I fix this problem, does anybody know?

---

### Post by Treebeard on 2006-02-24
Maybe you could try by installing these packages if they aren't installed :
[CODE]
$ sudo apt-get install ttf-arabeyes xfonts-intl-arabic ttf-kacst
[CODE]

---

### Post by DarkB on 2006-03-03
make sure you do apt-get msttcorefonts, and that should do it ... the others mentioned by Treebeard are still better than the default though.

---

### Post by Xintruder on 2008-01-11
Hello guys,
I thought I'de reply to this instead of making a new post.

Although I'm using Gutsy 7.10, I have the same problem. I did the above commands, restarted the browser. I see the fonts terribly. IE shows better fonts and I'm new to ubuntu and don't know how to go over this. help!

Thanks in advance.

---

### Post by maher_79 on 2008-03-02
same problem here trying to view arabic fonts in Firefox, anyone know what font packaged do we need?

Thanks!

---

### Post by nejad.62 on 2008-03-06
I install 7.10 , but the same issue for me. The text  in BBC new (Persian ) is not readable.:(

---

### Post by maher_79 on 2008-03-06
I did figure this one out.  Just install the "Ubuntu extra plugins" (i think that is what it is called) from the "add/remove programs" menu and you are all set! 

Enjoy :guitar:

---

### Post by lifeheart on 2008-03-12
> **maher_79 said:**
> I did figure this one out.  Just install the "Ubuntu extra plugins" (i think that is what it is called) from the "add/remove programs" menu and you are all set! 

Enjoy :guitar:

yes that is the right solution for this issue 

go to System --> then go to Administration -->  and select --> Synaptic Package Manager it will open new window 

use the search feature to find the package "ubuntu-restricted-extras"  

it include Microsoft fonts and other stuff such as support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

right click on the package and select mark for Installation and then click on apply! 

close the browser and open it again. (Works With Lunix Internet Explorer 6.0)  Still did not work with fierfox

---

### Post by maher_79 on 2008-03-12
> **lifeheart said:**
> 
close the browser and open it again. (Works With Lunix Internet Explorer 6.0)  Still did not work with fierfox

Worked with FireFox for me though!

---

### Post by lifeheart on 2008-04-03
yep it worked with FireFox after closing and starting the browser again lol, :)

---

