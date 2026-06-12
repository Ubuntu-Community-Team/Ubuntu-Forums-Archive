---
title: "[SOLVED] Conky hr question"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by santiagoward2000 on 2007-12-17
Hi people!
I've been trying to config my Conky. It went quite well, and I'm quite happy with it. However, there's one small thing I couldn't figure out. There's a horizontal line (hr) after the **SYSTEM** title. I wanted to add a Xubuntu logo at the end of that line, but, as you can see on the screenshot, the logo is out of range (if you look carefully, you can see a small lightblue dot). Is there any way to make the hr shorter, so that the logo can be in place?
Thanks!

---

### Post by psyopper on 2007-12-17
You might try adding height and length values to the {hr} tag. The first number would be the height in pixels of the bar, the second would be the length in pixels of the bar. It may take some math if you have set a fixed width of the conky window. The line would look something like 
```

${color green}SYSTEM ${hr 2,150}${color} ${color lightblue}${font OpenLogos:size=25}{${font}${color}

```

In this example your horizontal rule would be 2 pixels tall and 150 pixels wide. Play with the width number to adjust. You could also try using *alignr* or *alignc* tags to align elements to the right or center repsectively. Also, take a look in the [Super Ubuntu Conky.rc]("http://ubuntuforums.org/showthread.php?t=281865") thread for a LOT of tips and tricks.

---

### Post by santiagoward2000 on 2007-12-17
> **psyopper said:**
> You might try adding height and length values to the {hr} tag. The first number would be the height in pixels of the bar, the second would be the length in pixels of the bar. It may take some math if you have set a fixed width of the conky window. The line would look something like 
```

${color green}SYSTEM ${hr 2,150}${color} ${color lightblue}${font OpenLogos:size=25}{${font}${color}

```

In this example your horizontal rule would be 2 pixels tall and 150 pixels wide. Play with the width number to adjust. You could also try using *alignr* or *alignc* tags to align elements to the right or center repsectively. Also, take a look in the [Super Ubuntu Conky.rc]("http://ubuntuforums.org/showthread.php?t=281865") thread for a LOT of tips and tricks.

Thanks psyopper for the answer!
However, changing **{hr 2}** to **{hr 2 150}** didn't work. I tried different values for the second term, but the line would still occupy all the lenght, no matter what number I tried... :(

---

### Post by santiagoward2000 on 2007-12-17
OK. I could get the logo where I wanted using a negative offset. But now the logo and the horizontal line are overlapping. Is there any way to choose the line's length?

---

### Post by psyopper on 2007-12-21
> **santiagoward2000 said:**
> Thanks psyopper for the answer!
However, changing **{hr 2}** to **{hr 2 150}** didn't work. I tried different values for the second term, but the line would still occupy all the lenght, no matter what number I tried... :(

I think the tag should be **{hr 2,150}**. You are missing the comma between the values. I am still not sure it will work though...

Edit: Nope, still doesn't work. And now that I took the time to [RTFM]("http://conky.sourceforge.net/variables.html") I understand why:
> hr 	(height) 	 Horizontal line, height is the height in pixels

Apparently there is no way to fix the length of the line. You might try fooling around with blank spaces at the end of the line.

---

### Post by santiagoward2000 on 2007-12-21
> **psyopper said:**
> I think the tag should be **{hr 2,150}**. You are missing the comma between the values. I am still not sure it will work though...

Edit: Nope, still doesn't work. And now that I took the time to [RTFM]("http://conky.sourceforge.net/variables.html") I understand why:


Apparently there is no way to fix the length of the line. You might try fooling around with blank spaces at the end of the line.

Well, too bad... I'll try doing it with blank spaces then!
Thanks!

---

