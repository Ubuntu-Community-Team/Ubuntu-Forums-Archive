---
title: "ati big desktop, font problems"
date: 2006-05-21
forum: Desktop Environments
---

### Post by r12dk on 2006-05-21
Hello people

just installed lastest dapper on my desktop, with ati x600 card and two 19" lcd monitors. I got big desktop working with xinerama, so no 3d.

i assume thats why fglrxinfo gives "mesa project".

theres some small problems with the big desktop, for example the login screen spands over both monitors, and maximazeing windows likewise.
Any ideas?

And next, my fonts look ulgy, compared to my ubuntu laptop, that has really nice and smooth looking fonts. My laptop runs real fglrx with 3d support, can this be the problem?

If so, is it possible to run ubuntu with big desktop with 3d?

I dont really need 3d (would be nice though) i mostly care about getting the fonts nice looking. Some ideas?

thanks, Peter.

---

### Post by Fass on 2006-05-21
Are you sure you're running at the native resolution of the monitors? Also, for better fonts, add this to your ~/.fonts.conf:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>

<!-- Disable Autohinting for bold fonts -->

        <match target="font">
                <test name="weight" compare="more">
                        <const>medium</const>
                </test>
                <edit name="autohint" mode="assign"><bool>false</bool></edit>
        </match>

</fontconfig>
```

---

### Post by r12dk on 2006-05-21
Thanks

I tryed to write the code to .fonts.conf, dident seem to help.

I dont know, its like its one big screen:

```

peter@tuxCode:~$ xdpyinfo | grep resolution
  resolution:    97x96 dots per inch
peter@tuxCode:~$ xdpyinfo | grep dimensions
  dimensions:    2560x1024 pixels (670x271 millimeters)

```

Is it possible to get the big desktop to act like in windows?
I got nice font rendering on my dapper laptop by following this guide
[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)
but it dont work with this setup.

---

