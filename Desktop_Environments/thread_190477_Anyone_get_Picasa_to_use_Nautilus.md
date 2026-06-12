---
title: "Anyone get Picasa to use Nautilus"
date: 2006-06-06
forum: Desktop Environments
---

### Post by eeclark on 2006-06-06
Has anyone been successful in getting Picasa to use the nautilus file manager instead of Winefile?

---

### Post by eeclark on 2006-06-06
This is the message I get in Picasa:

Picasa was unable to open your native file browser. We will instead browse this directory with the Winefile utility. Please see picasa/desktop/picasa-hook-filehandler.sh template for instructions on how to use your own file manager.

I cannot find this file picasa-hook-filehandler.sh.

Has anyone had success?

---

### Post by eeclark on 2006-06-06
Found the file (it was named .template at the end and that is why locate did not find it):
Contents of the file: opt/picasa/desktop/picasa-hook-filemanager.sh.template
```

#!/bin/bash
#---------< Hook File >------------------------------------------------------
#
#       Picasa 'Hook' file to allow Picasa to be more closely
#   integrated with your desktop.
#
#   Picasa tries to integrate nicely with the Linux desktop where
#   and when it can.  However, Linux does not have standard or
#   well defined interfaces for many functions.
#
#   These hook files are provided by Google to allow users to
#   fine tune their integration of Picasa with their particular
#   Linux desktop environment.
#
#---------< hook-filemanager >------------------------------------------------
#
#   picasa-hook-filemanager.sh
#
#   This script is passed a command line with a single file name
#
#   The ideal behavior is for the file manager to open the directory
#   that contains that file, with that file highlighted.
#
#   If this script exits with a status of 0, then Picasa will
#   assume that you have handled the request, and will not perform
#   any further processing.
#
#   To use this file:
#       copy the picasa-hook-filemanager.sh.template file to
#       some place in your path, and name it picasa-hook-filemanager.sh.
#       Then edit the script to add the functionality you need
#
#----------------------------------------------------------------------------

exit 1


```

---

### Post by tflanders on 2006-12-15
Ok I edited the file and put it in /usr/bin but when I execute it it passes the whole directory and filename so nautilus errors off.

The error says this is not a folder location.

Which makes sense cause it tries to open the file in nautilus instead of opening the directory. 

Anyone have any hits of what should be in the file?


I have this

```
#!/bin/sh
nautilus $1
exit 0
```

---

### Post by tehu on 2006-12-17
try the meta-launcher

gnome-open $1

it works for me (file and directory)

---

### Post by Didjit on 2006-12-31
Hmm,I still can't get this working. Is this waht the file should look like and placed in /usr/bin/ ?



Didjit



#!/bin/sh
gnome-open $1
exit 0

---

### Post by shizeon on 2007-01-16
I got this semi working.  Right now nautilus doesn't support the selection of a file when opened via the commandline.  So this only opens the directory of the file, which is still better than nothing.  I found this on the upcoming nautilus feature page

[http://live.gnome.org/Nautilus#head-f2a0b4f437160b8659a4c3d4fdc655f89edbacc0]("http://live.gnome.org/Nautilus#head-f2a0b4f437160b8659a4c3d4fdc655f89edbacc0")
[INDENT]
"Satisfy beagle folks by making nautilus more scriptable.

    * Highlight files if passed as URI request.
    * (eg nautilus file:///home/gnome/file.txt will result in /home/gnome being opened and file.txt highlighted)[/INDENT]

So once this is implemented it can be even better.  For now, I did the following

```
gksudo gedit /opt/picasa/bin/picasa-hook-filemanager.sh
```

```

#!/bin/sh
nautilus "${1%%$(basename "$1")}" 

```

```
sudo chmod 775 /opt/picasa/bin/picasa-hook-filemanager.sh
```

---

### Post by gsmith on 2007-07-01
None of these worked for when I had spaces in my file / folder names.  This is what I'm using at the moment:

```
nautilus "$*"
exit 0
```

---

### Post by cheahk on 2007-07-23
This is pretty straightforward to do. First, create the hook-file.  

```

gedit picasa-hook-filemanager.sh

```

In that file, paste the following in:

```

#!/bin/sh
nautilus "${1%%$(basename "$1")}"

```

Finally, copy it to a directory in the path, and make it executable:

```

sudo mv picasa-hook-filemanager.sh /usr/local/bin
sudo chmod +x /usr/local/bin/picasa-hook-filemanager.sh

```

Now, if you really don't want to do all that, and want a copy and paste to make it work, just select, copy and paste the following:

```

sudo echo '#!/bin/sh' > /usr/local/bin/picasa-hook-filemanager.sh
sudo echo 'nautilus "${1%%$(basename "$1")}"' >> /usr/local/bin/picasa-hook-filemanager.sh
sudo chmod +x /usr/local/bin/picasa-hook-filemanager.sh

```

-K

---

### Post by Maverickprowls on 2007-09-22
Thanks very much Cheahk, this worked perfectly.

---

### Post by ÜbuntuMensch on 2007-10-09
Thanks, this is working nicely on Gutsy Beta 64 bit.

---

### Post by dustigroove on 2007-10-24
This worked for me, however Winefile still comes up in addition to the Nautilus window.

Any suggestions?

---

### Post by jayarsantos on 2008-03-18
thanks cheahk:popcorn:

---

