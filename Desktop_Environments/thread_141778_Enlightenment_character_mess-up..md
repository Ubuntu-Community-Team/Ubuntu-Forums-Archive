---
title: "Enlightenment character mess-up."
date: 2006-03-09
forum: Desktop Environments
---

### Post by sdide on 2006-03-09
Hi, 

I been running Ubuntu 5.10 for a while using a Gnome session. Now I wanted to try enlightenment and installed the E16 packages (0.16.6-3ubuntu3). All works fine execpt one thing - I need Danish characters, but they all display garbled in the my Eterms and various other apps. Any ideas where I should look for the problem? The problem wasn't there when I used Gnome.

My locale and /etc/console/boottime.kmap.gz seems to be set just fine.

 from the ~/.Eterm/themes/Eterm/user.cfg

begin multichar
    encoding iso-10646
    font 0 -misc-fixed-medium-r-normal--7-70-75-75-c-50-iso10646-1
    font 1 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso10646-1
    font 2 -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso10646-1
    font 3 -misc-fixed-medium-r-normal--14-130-75-75-c-70-iso10646-1
    font 4 -misc-fixed-medium-r-normal--15-140-75-75-c-90-iso10646-1
end multichar

Encoding iso-10646 ... doesn't really mean anything to me. I'm used to iso8859-1 or UTF-8....

Anyways after a bit of trial and error I gave up and went back to the gnome session. 

Any help appreciated.

Regards Søren Dideriksen

---

