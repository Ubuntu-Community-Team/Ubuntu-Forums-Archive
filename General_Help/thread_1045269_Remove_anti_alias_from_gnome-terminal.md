---
title: "Remove anti alias from gnome-terminal"
date: 2009-01-20
forum: General Help
---

### Post by bravemenrun333 on 2009-01-20
i like ubuntus anti aliasing of fonts on the desktop alot, but in a terminal there should be no anti aliasing. how can i disable it?
thanks for your help

---

### Post by Slim Odds on 2009-01-20
> **bravemenrun333 said:**
> i like ubuntus anti aliasing of fonts on the desktop alot, but in a terminal there should be no anti aliasing.

Why shouldn't there be? Anti-aliasing is GUI wide. Are you talking about the console?

---

### Post by Yashiro on 2009-01-20
Use a font that you have excluded from font smoothing in your fontconfig.

---

### Post by bravemenrun333 on 2009-01-20
how do i exclude such fonts? which file is it exactly?

---

### Post by bravemenrun333 on 2009-01-22
can anyone help me please?

---

### Post by Slim Odds on 2009-01-22
> **bravemenrun333 said:**
> can anyone help me please?

Can you rephrase the problem?

Consoles do not use anti-aliasing, the GUI does.

What seems to be the problem?

---

### Post by mcduck on 2009-01-22
If you want to run a terminal emulator with no antialiasing why not just use one that doesn't have any?

xterm, eterm, aterm, rxvt and so on.. at least xterm is included in the default install.

If you are talking about TTY's, there is no antialiasing. If your font's don't look crisp you are running at wrong resolution and your display is causing the blurring.

---

### Post by Slim Odds on 2009-01-22
> **mcduck said:**
> If you want to run a terminal emulator with no antialiasing why not just use one that doesn't have any?

xterm, eterm, aterm, rxvt and so on.. at least xterm is included in the default install.

If you are talking about TTY's, there is no antialiasing. If your font's don't look crisp you are running at wrong resolution and your display is causing the blurring.

My thoughts exactly.....

---

### Post by cpitchford on 2009-10-31
Just a thought, but I enable the bitmapped font fixed which is used by xterm.. For a system wide change, add this file to 
/etc/fonts/conf.d/69-zzz_fixedfonts.conf

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!-- Enabled Fixed bitmap fonts -->
  <selectfont>
    <acceptfont>
      <pattern>
        <patelt name="family"><string>Fixed</string></patelt>
      </pattern>
    </acceptfont>
  </selectfont>
</fontconfig>

then run:

dpkg-reconfigure fontconfig-config ; dpkg-reconfigure fontconfig; probably a good idea to restart X too.. just to be safe

See my original post with details from july 2008:

[http://ubuntuforums.org/showthread.php?t=304293](http://ubuntuforums.org/showthread.php?t=304293)

Now selecting fixed, semi-condensed, 10 gives gnome-terminal that xterm font flavor :) 

which was nice..

---

