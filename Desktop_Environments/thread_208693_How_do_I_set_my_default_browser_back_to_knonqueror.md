---
title: "How do I set my default browser back to knonqueror?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by lastexyle on 2006-07-03
I set firefox as my default browse through the firefox preference window, and it's caused me quite a bit of trouble. Half of my applications ignore it anyway (Kopete still uses konqueror) and others just don't work right (Konversation sends ~/'example.com' for example, which obviously doesn't work), So I'd like to just go back to using Konqueror as my default web browser. The problem is I can't find a way to do so. System Settings doesn't have anything for the default browser that actually helps (either the default or manually putting in konqueror doesn't work) and Konqueror it'self doesn't seem to have a "Set as default browser" option. Does anyone know how to fix this?

Thanks.

---

### Post by llamakc on 2006-07-04
I only know how to check/change it the Debian way. Open a Terminal.

Type:

update-alternatives --list x-www-browser

That will spit out your choices. Mine shows:

```

ken@dothan:~$ update-alternatives --list x-www-browser
/usr/bin/firefox
/usr/bin/opera

```

Now, do this:

```

ken@dothan:~$ sudo update-alternatives --config x-www-browser
Password:

There are 2 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/firefox
*+    2        /usr/bin/opera

Press enter to keep the default
[*], or type selection number:

```

So you would just select the # for konq at that point. That should make other programs behave. IF there's a KDE specific way, I don't know it. HTH.

---

### Post by lastexyle on 2006-07-04
Thanks, but that didn't work. It already said Konq qas the default browser and FF still thinks it's the default browser so there's gotta be something elsewhere.

---

### Post by NeoChaosX on 2006-07-04
Go to System Settings > KDE Components > Default Applications > Web Browser and make sure that "in an application based on the contents of the URL" is selected.

---

