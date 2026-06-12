---
title: "Nautilus: Completely Strange Sort Order"
date: 2011-02-10
forum: Desktop Environments
---

### Post by gacl on 2011-02-10
Hello, all,

The sort order in Nautilus is completely strange. What should be:

004
02
030
1
10

shows up as:

1
02
004
10
030

As far as I've been able to investigate this is a _years_ old bug which remains unfixed. Any workarounds? This is incredibly annoying!

Thanks.

Gus

---

### Post by coffeecat on 2011-02-10
I hate to tell you this but Windows 7 and MacOS (arrange in name order) display them in the same order.

---

### Post by gacl on 2011-02-11
Well, I've never used Windows 7 or MacOS and I've never encountered such a sort order before. All my files (which figure in the thousands) have been named accordingly. I've actually been unable to find files that I know are there because of this. I mean, when we add numbers, letters, and symbols it's completely impossible to find anything. I need this solved, please.

Once again, this is a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=355152](https://bugzilla.gnome.org/show_bug.cgi?id=355152). Any sensible workarounds?

Gus

---

### Post by coffeecat on 2011-02-11
That's an interesting bug report. I can see the logic in the way Nautilus (and Windows and MacOS) are sorting file names, but I can see the reason why people would want strict ASCII sorting.

I'm posting from Kubuntu Natty Alpha at the moment. I'm no great fan of KDE but I like to see how KDE4 is progressing. Dolphin, the KDE file manager, displays files sorted in the way you prefer. So does something called 'rekonq', which I guess is some sort of konqueror respin - you can tell how much I use KDE!

Using KDE instead of Gnome is not much of a workaround, but this has intrigued me enough to try Xubuntu and see what Xfce's Thunar makes of all this.

---

### Post by coffeecat on 2011-02-11
I tried booting from a Xubuntu 10.10 live CD. Thunar sorts the files in the same way as Nautilus, Windows and MacOS, so unfortunately installing Thunar in gnome won't help you.

---

### Post by gacl on 2011-02-11
I tried [this]("http://www.subdude-site.com/WebPages_Local/RefInfo/Computer/Linux/LinuxGuidesByBlaze/Nautilus_Guide/NautilusGuideBlaze.htm"), but it didn't work. Maybe .gnomerc is not being read?

Gus

---

### Post by asmoore82 on 2011-02-11
> **gacl said:**
> As far as I've been able to investigate this is a _years_ old bug which remains unfixed. Any workarounds? This is incredibly annoying!

Bug: *_**[COLOR="Purple"]No![/COLOR]**_*

Workaround: Yes!

> **gacl said:**
> Once again, this is a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=355152](https://bugzilla.gnome.org/show_bug.cgi?id=355152). Any sensible workarounds?

This is not a bug, this is by design: groups of digits are sorted in numeric order.

"groups of digits" is the key phrase. If you don't want the groups
of digits recognized as larger numbers, simply un-group them:
```
for file in *.*
do
    ext="${file##*.}"
    name="${file%.*}"
    new="$( echo "$name" | sed 's/./& /g' )"
    mv -iv "$file" "$new.$ext"
done
```

---

### Post by Krytarik on 2011-02-13
Wouldn't that fix your problem?:
[http://ubuntuforums.org/showthread.php?p=10431724](http://ubuntuforums.org/showthread.php?p=10431724)

It's also a post by asmoore82, I wonder why he/she didn't mention that in your case. But it has of course some negative side-effects, regarding case-sensitive sorting.

---

### Post by asmoore82 on 2011-02-13
> **Krytarik said:**
> Wouldn't that fix your problem?:
[http://ubuntuforums.org/showthread.php?p=10431724](http://ubuntuforums.org/showthread.php?p=10431724)

It's also a post by asmoore82, I wonder why he/she didn't mention that in your case. But it has of course some negative side-effects, regarding case-sensitive sorting.

I tested and had to go back and add to that post, even with LC_COLLATE=C,
nautilus still detects numbers and sorts them in ascending order.

I agree w/all that nautilus needs some user preferences for sorting, but
folks need to stop filing bug reports w/Gnome and instead file a "feature request."
Whining about "what Windows Explorer does" in the bug reports isn't constructive either.

---

### Post by phibuntu on 2011-06-07
Same problem here

setting "LC_COLLATE=C" in an executable file called "~/.gnomerc" does not help; or is completely ignoed.

Using Ubuntu 11.04, GNOME nautilus 2.32.2.1

Unfortunately libreoffice and others open a nautilus-Window to choose import files (like images).


Any workaround?

---

