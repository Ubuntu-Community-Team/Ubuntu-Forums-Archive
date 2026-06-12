---
title: "Viewing Chinese web pages doesn't work for me"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Arcocer on 2005-12-18
Hi all, I need to view chinese web pages (eg. [www.msn.com.cn](www.msn.com.cn)) but the characters are not visible, they appear as little squares with numbers. 

I have added Chinese language support via Synaptic Package manager (language-support-zh) but that didn't help.  I'm not looking to use the chinese version of the OS, just to be able to view the web pages correctly.

Any ideas?

Thanks,
Arcocer.

---

### Post by Ampersand on 2005-12-18
If you're using firefox, have you tried going to 'View - Character encoding - Auto-detect - Chinese'? There'll be a similar option if you're using a different browser.  If that doesn't work, try going through some of the other languages available under 'More encodings - East Asian'.

---

### Post by khc on 2005-12-18
Which site(s) are you trying to visit?

---

### Post by Arcocer on 2005-12-20
Hi, the address I'm trying to open is [http://www.msn.com.cn](http://www.msn.com.cn).

I tried setting the automatic recognition as suggested, and tried all character encodings available but its always the same result - no chinese characters, only little squares with numbers in.

From the html-source of the web page I see "charset=gb2312"
but if I choose this, it still does not display properly.

thanks for any help, 
James

---

### Post by khc on 2005-12-22
Works fine here. Can you check what font settings do you have in firefox for simplified chinese? What if you copy and paste some characters to gedit?

---

### Post by Arcocer on 2005-12-22
In firefox I have selected Character Encoding>Chinese Simplified GB-2392.
The font (edit>general>preferences>Fonts & colors) for simplificed chinese is "Sans serif". 

If I paste some chinese text from the web site into gedit, then I get the same squares with numbers in that I had on the web page - as if the font didn't have the glyphs.

Im going to try to uninstall and reinstall the language support...
James

---

### Post by anil_robo on 2005-12-23
I install Breezy just yesterday due to some hard drive problems. I had selected United States as my country, and American English as the default language. I visited the website you're trying to visit ([http://www.msn.com.cn]("http://www.msn.com.cn")) and here's how it looks like:
[ATTACH]4787[/ATTACH]

MY character encoding in firefox is Western ISO 8859.

---

### Post by khc on 2005-12-24
Is ttf-arphic-gbsn00lp installed?

---

### Post by Arcocer on 2005-12-25
Yes! Thats it ttf-arphic-gbsn00lp was missing! Thanks khc and to everyone who contributed to the thread - the fonts I had didn't have the characters defined!  

James

---

