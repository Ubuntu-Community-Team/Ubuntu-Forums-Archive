---
title: "can I use beryl and compiz?"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by lukanikos on 2007-07-09
Can I use Beryl and Compiz without uninstalling one of them?
Can I go one with both of them in my system?
I have an ATI 9600 card.

---

### Post by ajgreeny on 2007-07-09
Using the ati graphic driver that I expect Ubuntu installed by default on system install, you should be able to use either compiz or beryl on your system, they both work on mine with an ati 9200 card.  Be warned, however, beryl is still experimental and can sometimes cause problems with strange effects on windows and panels.  You do not need to uninstall compiz to use beryl or vice-versa, you simply chose which with the beryl-manager red jewel icon in the panel.  You can't use both together at the same time, of course.
For what it's worth, I think they both look great, but they don't actually make the system any more easy or productive to use, so I don't use either of them except to show what is possible to others.

---

### Post by ForensicBroom on 2007-07-09
How did you manage to make beryl and compiz work on 9200?? I get an error that pixmap is not supported, or something like that :confused:

---

### Post by ajgreeny on 2007-07-09
Sorry, but I have absolutely no idea!  Compiz worked by enabling desktop effects from the menu, and beryl and beryl-manager just worked if I wanted after installing them with synaptic.  Having seen them both in action I now don't actually use either of them.

---

### Post by ForensicBroom on 2007-07-09
Strange, because when I go to system -> preferences -> desktop effects, and go to enable desktop effects, the whole screen gets white when I use the default mesa drivers. When I install ATI drivers, it says: "Can't enable desktop effects!", when I install beryl the titlebars appear to be missing, and when I install compiz and run it with compiz --replace in terminal it says something like fatal error, texture_from_pixmap not supported... Tommorow I'm getting a nVidia so I think it will work :)

---

### Post by amadeus266 on 2007-07-09
> **ForensicBroom said:**
> Strange, because when I go to system -> preferences -> desktop effects, and go to enable desktop effects, the whole screen gets white when I use the default mesa drivers. When I install ATI drivers, it says: "Can't enable desktop effects!", when I install beryl the titlebars appear to be missing, and when I install compiz and run it with compiz --replace in terminal it says something like fatal error, texture_from_pixmap not supported... Tommorow I'm getting a nVidia so I think it will work :)

You probably have the reduced version of the 9200. My AIW9200 w/ 128MB works fine.

---

### Post by ajgreeny on 2007-07-11
You could be right, amadeus266, because lshw gives the following info on my card:-

description:   VGA compatible controller
  product:   RV280 [Radeon 9200 PRO]
  vendor:   ATI Technologies Inc
  physical id:   0
  bus info:   pci@02:00.0
  logical name:   /dev/fb0
  version:   01
  size:   128MB
  width:   32 bits

so I guess I have a better version of the 9200 than ForensicBroom or lukanikos.

---

