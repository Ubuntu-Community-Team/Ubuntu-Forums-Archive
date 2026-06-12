---
title: "Where are the fonts settings stored?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by Lukas666 on 2009-11-28
Hello!

I want to experiment a bit with fonts settings, in particular the following screens:

[http://www.techotopia.com/index.php/Configuring_Ubuntu_Desktop_Fonts](http://www.techotopia.com/index.php/Configuring_Ubuntu_Desktop_Fonts)

But I would prefer to backup my current settings first, in case something goes wrong. Is there a file where all those options are kept?

Ubuntu 9.10 (64bit)

Thanks,
L.

---

### Post by gettinoriginal on 2009-11-28
System wide fonts are on the directory '/usr/share/fonts/'.

---

### Post by Lukas666 on 2009-11-28
Thanks, but I don't think these are system wide settings. I can change them without root password.

---

### Post by falconindy on 2009-11-28
Your particular font settings are buried in:

$HOME/.gconf/desktop/gnome/interface/%gconf.xml

---

### Post by Lukas666 on 2009-11-29
> **falconindy said:**
> Your particular font settings are buried in:

$HOME/.gconf/desktop/gnome/interface/%gconf.xml

Thanks.

You would think, but this is not entirely true.

I changed all 5 fonts and only 3 changes ended up in the file you mentioned.

```
<entry name="monospace_font_name" mtime="1259475509" type="string">
        <stringvalue>Monospace 14</stringvalue>
    </entry>
    <entry name="document_font_name" mtime="1259475499" type="string">
        <stringvalue>Sans 11</stringvalue>
    </entry>
    <entry name="font_name" mtime="1259291197" type="string">
        <stringvalue>Sans 10</stringvalue>
    </entry>

```I have no idea where 2 others ("desktop font" and "window title font") go.

L.

---

### Post by Lukas666 on 2009-11-29
> **Lukas666 said:**
> Thanks.

I have no idea where 2 others ("desktop font" and "window title font") go.



Ok, "desktop font" is defined here:

$HOME/.gconf/apps/nautilus/preferences/%gconf.xml

```

<entry name="desktop_font" mtime="1259475502" type="string">
        <stringvalue>Sans 12</stringvalue>
</entry>

```

and the last one in 

$HOME/.gconf/apps/metacity/general/%gconf.xml:

```

<entry name="titlebar_font" mtime="1259475505" type="string">
        <stringvalue>Sans Bold 13</stringvalue>
</entry>

```

---

