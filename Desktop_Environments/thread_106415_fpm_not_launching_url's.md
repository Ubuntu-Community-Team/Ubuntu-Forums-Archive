---
title: "fpm not launching url's"
date: 2005-12-20
forum: Desktop Environments
---

### Post by thk on 2005-12-20
I've used fpm (Figaro's Password Manager) to manage passwords for years (wish there was a better alternative). For some reason, it is no longer launching url's when I double click on an entry. (I've double checked the launcher settings and they are correct.) I miss this capabilty greatly. Oddly, it does work on my laptop running Ubuntu, but not my work machine. (Both use 5.10.) Has anyone else noticed this behavior?

---

### Post by matthew on 2005-12-20
I'm sorry I can't help with the fpm problem as I've not used it, but there is another password manager program you might be interested in trying out if you use Gnome. It's called called Revelation Password Manager and is available in the repositories (package name is "revelation"). It has the functionality you describe.

---

### Post by thk on 2005-12-20
I've installed revelation. It segfaults when importing fpm files. :(

---

### Post by matthew on 2005-12-20
Bummer. That means in order to use Revelation you would have to input everything from scratch...that doesn't sound fun. Does it work well otherwise? or shall we put out a call for more ideas?

---

### Post by thk on 2005-12-21
I think it has the most potential for the gnome desktop. There are still problems. On first install, if run from the desktop menu, it will issue an error saying "cannot find configuration information" and die. It can be run from the command line however, and will run from the desktop menu after that. There is also a warning on the command line about using gnome.vfs python module which is deprecated. Only major snafu is it wont import from fpm. I would have switched otherwise.

---

### Post by thk on 2005-12-21
Here's the output on importing from fpm:

Traceback (most recent call last):
  File "/usr/bin/revelation", line 183, in <lambda>
    "file-import"		: lambda w: self.file_import(),
  File "/usr/bin/revelation", line 1162, in file_import
    entrystore = self.__file_load(file, None, datafile)
  File "/usr/bin/revelation", line 786, in __file_load
    return datafile.load(file, password, lambda: dialog.PasswordOpen(self, os.path.basename(file)).run())
  File "/usr/lib/python2.4/site-packages/revelation/io.py", line 113, in load
    entrystore = self.__handler.import_data(data, password)
  File "/usr/lib/python2.4/site-packages/revelation/datahandler/fpm.py", line 244, in import_data
    content = self.__decrypt(cipher, util.dom_text(fieldnode))
  File "/usr/lib/python2.4/site-packages/revelation/datahandler/fpm.py", line 59, in __decrypt
    decoded += chr(high * 16 + low)
ValueError: chr() arg not in range(256)

---

