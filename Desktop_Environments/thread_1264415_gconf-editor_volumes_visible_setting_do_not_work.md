---
title: "gconf-editor volumes visible setting do not work"
date: 2009-09-12
forum: Desktop Environments
---

### Post by szarywilq on 2009-09-12
Hi,

Always after installation of Ubuntu, my first two steps are setting fstab to automatically mount ntfs drives at boot, and using gconf-editor to disable volumes visible option. Few days ago I had to re-install system. Everything works, except those volumes. All settings in gconf-editor which are about icons visible on desktop (trash, home, computer icon etc) do not work. Default is - only volumes are visible. And I can't change it, I can't remove them nor add other icons.

---

### Post by Brascocampbell on 2009-09-12
my gconf problem is similar. all i have is my desktop background and nothing else cant do anything with it.
my error code is 3354
where to go?

---

### Post by szarywilq on 2009-09-14
bump. Any ideas?

---

### Post by drs305 on 2009-09-14
Is the desktop turned on? If the Desktop acts like there is a glass pane over it, the Desktop is probably turned off. The Desktop setting is the 'master' - the rest won't work if it isn't on.
```

gconf-editor /apps/nautilus/preferences/show_desktop
*or if you just want to run the command that turns it on:*
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'

```

Are you running compiz?

---

### Post by szarywilq on 2009-09-15
1. show_desktop was TRUE

2. Compiz is completely uninstalled. I have ATI card so I always had problems with it. And I do not need visual desktop effects.

EDIT:
When I set show_desktop to FALSE - volumes icons still on desktop.

---

### Post by szarywilq on 2009-09-16
bump

---

### Post by szarywilq on 2009-10-04
Ok, it is working. I can add or remove icons like trash or home from desktop through gconf.

But during some changes I incidentally pressed "use this key as obligatory" (or something like that I have polish version).

So now, tab apps/nautilus/desktop genarally works. But volumes visible is "protected from writing" (or something like that). How can I change it?

---

### Post by drs305 on 2009-10-04
> **szarywilq said:**
> Ok, it is working. I can add or remove icons like trash or home from desktop through gconf.

But during some changes I incidentally pressed "use this key as obligatory" (or something like that I have polish version).

So now, tab apps/nautilus/desktop genarally works. But volumes visible is "protected from writing" (or something like that). How can I change it?

If you mean that you have made a change to a gconf key and don't know how to 'reset' it, right click on the value, then select "Unset Key". This will return the entry to the default value.

---

### Post by szarywilq on 2009-10-04
I tried it first. Didn't worked. I do not know why. This is why I asked here. Then I read somewhere else on the net, that this option SHOULD restore it. So I restarted system, and yes, it worked. Key was unlocked.
But still, when it is set to false, icons are still on desktop.

I'm gonna pass, volumes on desktop are not worth it.

Thanks for all advices.

---

