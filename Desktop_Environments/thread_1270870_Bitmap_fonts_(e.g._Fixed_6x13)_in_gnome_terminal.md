---
title: "Bitmap fonts (e.g. Fixed 6x13) in gnome terminal"
date: 2009-09-20
forum: Desktop Environments
---

### Post by pmorch on 2009-09-20
Hi,

As others, I insist on using the 6x13 bitmap font (from xterm) in my gnome-terminal. This is how to do it in Jaunty:
[LIST]
[*] cd /etc/fonts/conf.d
[*] rm 70-no-bitmaps.conf
[*] ln -s ../conf.avail/70-yes-bitmaps.conf .
[*] dpkg-reconfigure fontconfig
[*] logout & restart X / gdm (e.g. reboot)
[*] Choose font: Fixed Semicondensed 10
[/LIST]

( Perhaps "dpkg-reconfigure fontconfig-config" is required too, choosing to enable bitmap fonts at the 3rd question. I don't think so but I did a lot of tinkering to get at the above! :P )

== Background ==

This pretty much comes from:
[http://grahams.free-online.co.uk/mediawiki/index.php/Ubuntu_Bitmap_Fonts](http://grahams.free-online.co.uk/mediawiki/index.php/Ubuntu_Bitmap_Fonts) except that my experience was that I needed to restart X before the "Fixed" font selection showed up.

In releases before Jaunty, I could follow [http://ubuntuforums.org/showthread.php?t=224263](http://ubuntuforums.org/showthread.php?t=224263) and [http://ubuntuforums.org/showthread.php?t=304293](http://ubuntuforums.org/showthread.php?t=304293) but that doesn't work in Jaunty. The above does. I do so wish that bitmapped fonts would be enabled by default in the gnome terminal, but it hasn't happened for years! :)

---

### Post by cpitchford on 2009-10-31
I'm on a mission to push an alternative solution.. 

What you've done is enabled all bitmap fonts, which (for me) causes rendering problems in things like firefox.. 

I've added a different file to 
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

dpkg-reconfigure fontconfig-config ; dpkg-reconfig fontconfig
then restart X

This enables JUST the fixed fonts. Using Fixed, semi-condensed, 10 gives gnome-terminal that familiar xterm look and feel :) 

This saves enabling all those pesky bitmapped fonts

I think the difference between my original post in the thread mentioned above is running the dpkg-reconfigure for both fontconfig-config AND fontconfig.. 

running just fontconfig-config didn't seem to enable the fix for me when I tried it on my upgraded 9.10 box today.. hence more research :)

---

### Post by dpb on 2010-04-29
> **cpitchford said:**
> I'm on a mission to push an alternative solution.. 

What you've done is enabled all bitmap fonts, which (for me) causes rendering problems in things like firefox.. 

I've added a different file to 
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

dpkg-reconfigure fontconfig-config ; dpkg-reconfig fontconfig
then restart X

This enables JUST the fixed fonts. Using Fixed, semi-condensed, 10 gives gnome-terminal that familiar xterm look and feel :) 

This saves enabling all those pesky bitmapped fonts

I think the difference between my original post in the thread mentioned above is running the dpkg-reconfigure for both fontconfig-config AND fontconfig.. 

running just fontconfig-config didn't seem to enable the fix for me when I tried it on my upgraded 9.10 box today.. hence more research :)

[SIZE="4"]THANKS!![/SIZE]

Just tried this with 10.04 (Lucid RC), and it still works.  FYI, to get gnome-terminal to show 6x13, I didn't even need to restart X.  Just dpkg-reconfigure (both packages) was needed.

---

