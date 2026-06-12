---
title: "How do I install PCF fonts?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Senesence on 2006-10-01
Im trying to install Triskweline: [http://www.netalive.org/tinkering/triskweline/](http://www.netalive.org/tinkering/triskweline/)

I already tried taking the trisk.pcf and placing it in the /usr/share/fonts directory, and then running sudo dpkg-reconfigure fontconfigure. But the font  still doesn't show up as an option in the text editor (gedit).

What am I doing wrong? Please help me figure this out.

Thank you.

---

### Post by dragonfyre13 on 2006-10-02
[http://www.xfree86.org/current/fonts2.html#3](http://www.xfree86.org/current/fonts2.html#3)

This is about as close as I have gotten to PCF fonts. There has to be way to install FON fonts though. They are windows specific. Otherwise, I would look into a converter or something to bring them from PCF to ttf or something.

---

### Post by dragonfyre13 on 2006-10-02
Oh, and make sure to turn on bitmap fonts by doing this.

run this. sudo dpkg-reconfigure fontconfig

I know you already did from our LENGTHY conversation on IRC, but I figured it would help others.

---

