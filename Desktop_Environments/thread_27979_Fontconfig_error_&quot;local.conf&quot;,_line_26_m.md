---
title: "Fontconfig error: &quot;local.conf&quot;, line 26: mismatched tag"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Shadar on 2005-04-18
I get this error when ever I load gedit from terminal and I'm wondering what it is? I've tried to look up local.conf but don't really know what to look for and where the local.conf actually is?

---

### Post by Alexander Kirillov on 2005-04-18
[QUOTE=Shadar]I get this error when ever I load gedit from terminal and I'm wondering what it is? I've tried to look up local.conf but don't really know what to look for and where the local.conf actually is?[/QUOTE]
 
It is in
/etc/fonts/local.conf
Probably some program messed it up. Post the full text of this file here (it is short) if you need further help.

---

### Post by Shadar on 2005-04-23
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->
  <match target="font">
    <test qual="all" name="rgba">
      <const>unknown</const>
    </test>
    <edit name="rgba" mode="assign"><const>rgb</const></edit>
  </match>
<!-- Uncomment below to enable the freetype autohinter module -->
<!--
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
<match target="pattern">
<test qual="any" name="family">
<string>Bitstream Vera Sans
</test>
<edit name="family" mode="assign">
<string>Verdana
</edit>
</match>
<match target="pattern">
<test qual="any" name="family">
<string>Helvetica
</test>
<edit name="family" mode="assign">
<string>Arial
</edit>
</match>
<match target="pattern">
<test qual="any" name="family">
<string>Palatino
</test>
<edit name="family" mode="assign">
<string>Georgia
</edit>
</match>
</fontconfig>

```

---

### Post by Alexander Kirillov on 2005-04-27
```

<match target="pattern">
<test qual="any" name="family">
<string>Bitstream Vera Sans
</test>
<edit name="family" mode="assign">
<string>Verdana
</edit>
</match>

```
I am not 100% sure what this (and similar) does, nor where it comes from - it is definitely not the default local.conf file. Probably one of extra packages you installed did this (maybe MS core fonts?). However, I do know that it is not valid XML: you have opening tag <string>, but no matching closing tag. You can try closing each of them, so the above becomes
```

<match target="pattern">
<test qual="any" name="family">
<string>Bitstream Vera Sans</string>
</test>
<edit name="family" mode="assign">
<string>Verdana</string>
</edit>
</match>

```

This woudl make it valid XML - but, as I said, I am not sure what it actually does...

---

### Post by Shadar on 2005-05-01
I should've noticed that myself... Thank you Alexander!

---

