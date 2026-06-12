---
title: "Firefox is not the default browser"
date: 2011-03-27
forum: Desktop Environments
---

### Post by StephGbzh on 2011-03-27
Hello all,

Despite my efforts, I cannot set Firefox to be my default browser in Ubuntu 10.10.
It used to be the default until I installed Chromium last year. Since then, Ubuntu Software Center, LibreOffice, EverNote (through Wine) and probably other apps open links in Chromium instead of Firefox.

I tried several solutions to no avail :
- System > Preferences > Preferred Applications : Web Browser = Firefox
I tried with the custom command too : "firefox %s" => still opens Chromium.
- Firefox internal preferences : firefox = default
- Chromium internal preferences : chromium is NOT the default
- stuff like "sudo update-alternatives --config x-www-browser" set to firefox => another fail
- uninstalling Chromium : that works, Firefox opens all the links. Obviously it is not the desired solution as I want to use Chromium too.
- in Gnome Configuration Editor, there are no mention of chromium and /desktop/gnome/url-handlers/http/command = firefox %s

I briefly hoped that I would get a solution from this [SOLVED] thread :
[http://ubuntuforums.org/showthread.php?t=1705389](http://ubuntuforums.org/showthread.php?t=1705389)
but the OP finds a magical solution which he cannot describe and thus I cannot use it .

Anyone having a hint or a suggestion is welcome! :confused:

---

### Post by Frogs Hair on 2011-03-27
When you attempted to reinstall Chrome did you remove all the files as well ? While looking for an answer I read that this needs to be done or the old profile settings just return.

It looks like you may have tried something similar to this , but I will post a link anyway. [http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/](http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/)

---

### Post by StephGbzh on 2011-03-27
Thanks for your help but none works.

I removed Chromium and the folder ~/.config/chromium
As mentioned above, all links open in Firefox at this point.
Then I reinstalled Chromium and it steals links opening again.

I checked again the "update-alternatives" and here are the results :

```
/usr/bin$ ll gnome-www-browser x-www-browser www-browser chromium-browser abrowser firefox
lrwxrwxrwx 1 root root    7 2011-03-25 19:52 abrowser -> firefox*
-rwxr-xr-x 1 root root 3438 2011-03-24 23:59 chromium-browser*
lrwxrwxrwx 1 root root   32 2011-03-25 19:52 firefox -> ../lib/firefox-3.6.16/firefox.sh*
lrwxrwxrwx 1 root root   35 2011-02-26 12:44 gnome-www-browser -> /etc/alternatives/gnome-www-browser*
lrwxrwxrwx 1 root root   29 2010-10-01 20:22 www-browser -> /etc/alternatives/www-browser*
lrwxrwxrwx 1 root root   31 2011-02-26 12:45 x-www-browser -> /etc/alternatives/x-www-browser*
/usr/bin$ ll /etc/alternatives/gnome-www-browser /etc/alternatives/www-browser /etc/alternatives/x-www-browser
lrwxrwxrwx 1 root root 16 2011-02-26 12:44 /etc/alternatives/gnome-www-browser -> /usr/bin/firefox*
lrwxrwxrwx 1 root root 17 2010-10-01 20:22 /etc/alternatives/www-browser -> /usr/bin/lynx.cur*
lrwxrwxrwx 1 root root 16 2011-02-26 12:45 /etc/alternatives/x-www-browser -> /usr/bin/firefox*
```

To be more precise, here are the results when opening an http URL from different applications with the hope that it will make any sense for someone :
- Ubuntu Software Center, LibreOffice Writer, Evernote (wine), Terminal : chromium
- Thunderbird, Tellico : firefox

When trying to understand how Terminal open links, I stumbled upon two commands : gnome-open and xdg-open.
Both open Chromium when I feed them an URL.
Do you know how they work ?

---

### Post by StephGbzh on 2011-03-27
Alleluiah ! I found the solution ! :KS

Based on this post : [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg869561.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg869561.html), I edited all firefox.desktop files I could find, namely :
```
~/.gnome2/panel2.d/default/launchers/firefox.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/applications/firefox.desktop
~/.gnome2/panel2.d/default/launchers/firefox-2.desktop
```
to add the MimeTypes found in chromium-browser.desktop :
```
x-scheme-handler/http;x-scheme-handler/https;
```
But it failed, even after a restart.

So I headed back to xdg-open which launches gvfs-open (gnome-open can be used if gvfs-open is not found).
Based on [https://bugs.archlinux.org/task/23237](https://bugs.archlinux.org/task/23237), I tried
```
xdg-mime query default x-scheme-handler/http
```
which returned nothing.
Then I did this to handle http with Firefox :
```
xdg-mime default firefox.desktop x-scheme-handler/http
```
And tada, it works !
All links open in Firefox ! :popcorn:

NB : Just for fun, I tried to set Chromium as my Preferred Browser and guess what, all links still open in Firefox... anyway I don't care, it's just that all these settings are overlapping each other in an all too complicated way.

---

### Post by castironpants on 2011-03-28
That did the trick! Thanks!

---

