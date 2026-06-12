---
title: "how do I find the files that go with a program?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ragesoss on 2005-10-14
I've installed (through synaptic) the program "dosbox," and I've found the binary in usr/bin.  How would I go about finding the rest of the files associated with it (readme and configuration files, particularly)?

Is there some sort of standard file location where the non-binary parts of programs go?

---

### Post by annibale on 2005-10-14
[QUOTE=ragesoss]I've installed (through synaptic) the program "dosbox," and I've found the binary in usr/bin.  How would I go about finding the rest of the files associated with it (readme and configuration files, particularly)?[/QUOTE]

Open synaptic, select the package "dosbox", click on Properties -> Installed files.

---

### Post by GeneralZod on 2005-10-14
Open Synaptic, find "dosbox" (or whatever the package was named), right-click on it and select Properties->Installed Files.

I don't have dosbox installed, so there are generic comments:

Usually, you won't care about where these files go; for example, manual pages are usually accessible through

```

man dosbox

```

or - fun konqueror tip! - entering

```

man://<program name>

```

as a konqueror URL! :)

The system-wide config files are stored in /etc - not all programs have system-wide configs, though.  Your personalised configs will be stored in your home directory;  in konqueror, go to ~ and click "Show Hidden Files" in the view menu, and you should see something like .dosbox in the list.

Hope this helps!

---

### Post by chandra on 2005-11-09
[QUOTE=ragesoss]I've installed (through synaptic) the program "dosbox," and I've found the binary in usr/bin.  How would I go about finding the rest of the files associated with it (readme and configuration files, particularly)?

Is there some sort of standard file location where the non-binary parts of programs go?[/QUOTE]

dpkg -L dosbox

If the output is too long, you can pipe it through less so:

dpkg -L | less

and use PageUp/Page Down to view.

---

