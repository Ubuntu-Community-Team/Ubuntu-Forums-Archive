---
title: "How to get windows fonts in opera"
date: 2008-07-02
forum: Desktop Environments
---

### Post by egos68 on 2008-07-02
I realy want to get windows fonts in opera.I probely got to downlaod the fonts some place..where?

Then i have to but it someplace in linux but where?

then i got to make operafind them but how?

please help me

---

### Post by jpeddicord on 2008-07-02
Moved from Tutorials and Tips, as it is a question.

---

### Post by ibutho on 2008-07-02
If you or a friend has a copy of Windows, you can copy your TT fonts from C:\Windows\Fonts onto a USB stick or other removable media. You can then copy the fonts into your ~/.fonts directory on Linux. If you want all users on your system to use the fonts, then instead of copying them to ~/.fonts, put them in a global directory e.g.[LIST=1]
[*]Create a driectory in /usr/local/share call msfonts
[*]Copy the fonts to /usr/local/share/msfonts
[*]Run Applications -> Accessories -> Terminal
[*]Enter ```
sudo -i 
```
[*]Enter```
cd /usr/local/share/msfonts 
sudo mkfontdir 
sudo mkfontscale 
sudo fc-cache
```
[/LIST]
When you log out and back in again you should be able to use the Windows fonts.

---

### Post by SEMW on 2008-07-02
If all you want is the basic Windows core fonts (Arial, Times New Roman, Tahoma etc.), you don't even need to do that -- just run
```
sudo apt-get install msttcorefonts
```
And they'll get automatically installed in the right place for you.  As a bonus, when you restart Opera, all the new fonts will populate themselves into your font choices in opera like magic; though I'm not sure why...!

---

### Post by egos68 on 2008-07-17
> **SEMW said:**
> If all you want is the basic Windows core fonts (Arial, Times New Roman, Tahoma etc.), you don't even need to do that -- just run
```
sudo apt-get install msttcorefonts
```
And they'll get automatically installed in the right place for you.  As a bonus, when you restart Opera, all the new fonts will populate themselves into your font choices in opera like magic; though I'm not sure why...!

Thanx very much.That was easy and worked like a charmed:guitar:

---

