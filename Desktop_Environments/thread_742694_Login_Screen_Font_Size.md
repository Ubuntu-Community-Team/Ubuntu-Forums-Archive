---
title: "Login Screen Font Size"
date: 2008-04-01
forum: Desktop Environments
---

### Post by EoinB on 2008-04-01
Hello,

I know there are a few of these questions floating about, but I have yet to come across one that offers a definitive solution or one that works for me.
On the login screen the text in the username box is very small, just readable, but very small. The text box labels are fine, as are the dots that cover up my password. The text in the menus is also very small as are any 'tooltips' (if that is the correct term for a box that appears after leaving the mouse over a field for a second).
I have been editing the .xml files in /usr/share/gdm/themes in an effort to rectify this issue but have not had any success. At one point I made the text colour white, which freaked me out for a second, but on selecting the text, it appeared the size had not been changed.
All the references to text size I can see in the .xml files seem reasonable, between 9 and 11. I am a little stumped. My current resolution is 1360x768 if that helps at all.
Any advice you can give would be most helpful.

Thanks in advance.

---

### Post by EoinB on 2008-04-03
Does nobody have any ideas on this?

---

### Post by EoinB on 2008-04-07
Still no ideas? 

I'll give up after this, since people clearly don't know or care.

---

### Post by edvar on 2008-04-12
I have the exact same problem and my screen resolution is also the same as yours

---

### Post by EoinB on 2008-04-13
Don't think we're likely to find help here.

:(

---

### Post by y-lee on 2008-04-13
I saw this thread when you first posted it but I did not know the answer. But i think the font size on login is determined by both your xorg.conf file (which sets video resolution) and by the theme you have selected for your login. Editing the xml files for the themes found at /usr/share/gdm/themes/ certainly should work. for the theme I use my font size is 12 tho i have a smaller screen resolution than you. 

> All the references to text size I can see in the .xml files seem reasonable, between 9 and 11.

For your screen resolution this seems small to me. Determine what theme you are using at login (system -->administration -->login Window) and back up that file. Now change references to font size to bigger numbers like 20. (you have to be super user to edit these files)

See [edgy Login screen font size changed?]("http://ubuntuforums.org/archive/index.php/t-332101.html")

Edit I am assuming you are using gnome and gdm here and not something else since this is ubuntus default install.

---

### Post by uterrorista on 2008-04-13
here, fonts are TOO BIG!
[http://farm3.static.flickr.com/2183/2404200886_76fbae1f6a_o.png](http://farm3.static.flickr.com/2183/2404200886_76fbae1f6a_o.png)

---

### Post by paul101 on 2008-04-13
@uterrorista can you get into a menu or something: if you can go to

System > Preferences > Appearance > Fonts select the font and change the font size :)

---

### Post by EoinB on 2008-04-14
Thanks for the reply. I'll have another nose around, see if I can get anywhere.

---

