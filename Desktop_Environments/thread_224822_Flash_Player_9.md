---
title: "Flash Player 9"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Magiczero on 2006-07-28
Hi

How do I install flash player I am stilling 7 and i need 9.  


Thank you!

---

### Post by kb3hkg on 2006-07-28
It has yet to be released breaking yet another promise from Macromedia. I have heard that the windows stand alone flash player will run through wine though.

---

### Post by roostishaw on 2006-07-28
As the above poster mentioned, you can run it through wine. Just get the latest firefox installer, run it through wine (leave the default install path). Then go to video.google.com and go to view any random video. When that bar appears at the top of the firefox window (the instance of firefox you're running through wine, of coarse), tell it to install flash player. That will give you Flash 9. From then on, if you need to run a flash file that only supports Flash 9, run the instance of Firefox you just installed. Run it with:
```
wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```
Tell me how it goes.

---

### Post by dubbreak on 2006-07-28
> **kb3hkg said:**
> It has yet to be released breaking yet another promise from Macromedia. I have heard that the windows stand alone flash player will run through wine though.

$post =~ s/Macromedia/Adobe/g;

---

### Post by roostishaw on 2006-07-28
> **dubbreak said:**
> $post =~ s/Macromedia/Adobe/g;
?

---

### Post by dubbreak on 2006-07-28
> **roostishaw said:**
> ?

Tongue in cheek, Adobe bought Macromedia, it is now Adobe flash player. Try the url [http://www.macromedia.com]("http://www.macromedia.com") (note: you are directed to adobe and there are links to dl the Adobe flash player). 
The syntax is just a perl swap (finds first expression and replaces it with second), not very funny when you have to explain it though :sad:.

---

### Post by roostishaw on 2006-07-28
Oh... right.

---

### Post by doobit on 2006-07-28
> **dubbreak said:**
> Tongue in cheek, Adobe bought Macromedia, it is now Adobe flash player. not very funny when you have to explain it though :sad:.

I thought is was funny. Adobe should make it a t-shirt.

---

### Post by mark2741 on 2006-07-28
If you must have player v9 (or 8, for that matter), then I recommend IEs4Linux over going the Wine route. It comes preinstalled with Flashplayer 9.

---

### Post by boast on 2006-07-28
> **Magiczero said:**
> Hi

How do I install flash player I am stilling 7 and i need 9.  


Thank you!
[http://www.howtoforge.com/ubuntu_flash_player](http://www.howtoforge.com/ubuntu_flash_player)

---

