---
title: "Zenity help with loading bar"
date: 2009-06-01
forum: General Help
---

### Post by monsterstack on 2009-06-01
Hi everyone. I have a zenity script to update some packages, and I'm having trouble getting the loading bar to work properly. Piping the command to Zenity like this:

```
wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list \ 
--output-document=/etc/apt/sources.list.d/medibuntu.list | \
   zenity --progress --auto-kill --auto-close \
   --text "Finding and installing the Medibuntu repositories..." &
```

doesn't seem to work properly, with or without the final &. Neither does starting the loading bar first as shown here:

```
zenity --progress --auto-kill --auto-close \
--text "Finding and installing the Medibuntu repositories..." &
  wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list \ 
  --output-document=/etc/apt/sources.list.d/medibuntu.list
```

The loading bar either shows up after the repositories have been installed, or it shows up first and refuses to go away even when the job is finished. Can anyone help?

---

### Post by mb_webguy on 2009-06-01
Well, it looks to me like you're just downloading the sources list, not the packages themselves.  If you don't believe me, just run the wget part by itself.

Since the zenity progress bar closes once it reaches 100%, and you're trying to download multiple files, I'd say your best bet would be to first get a listing of each file, then run a separate wget for each individual file, piping each into zenity.  Unfortunately, while you might be able to get a directory listing for a directory (depending on the web server's settings), it comes as an html file, which would have to be parsed to strip out the file names.  And your script would need to parse the file to identify and recurse directories as well, of course.

---

### Post by monsterstack on 2009-06-01
> **mb_webguy said:**
> Well, it looks to me like you're just downloading the sources list, not the packages themselves.  If you don't believe me, just run the wget part by itself.

Since the zenity progress bar closes once it reaches 100%, and you're trying to download multiple files, I'd say your best bet would be to first get a listing of each file, then run a separate wget for each individual file, piping each into zenity.  Unfortunately, while you might be able to get a directory listing for a directory (depending on the web server's settings), it comes as an html file, which would have to be parsed to strip out the file names.  And your script would need to parse the file to identify and recurse directories as well, of course.

No, I believe you. That's only the first part of the script. Later on I do apt-get updates and installs etc. I don't know what you mean about downloading mutliple files; wget only fetches [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) for me.

---

### Post by unutbu on 2009-06-01
This command comes from Twigman: [http://ubuntuforums.org/showpost.php?p=1850902&postcount=2:](http://ubuntuforums.org/showpost.php?p=1850902&postcount=2:)


Save this as ~/bin/wget_progress_meter.sh (or whatever you prefer):

```
#!/bin/sh
# Thanks to Twigman: http://ubuntuforums.org/showpost.php?p=1850902&postcount=2
wget "$@" 2>&1 | sed -u 's/.*\ \([0-9]\+\)%\ \+\(.*\)$/\1\n#Downloading \2/' | zenity --progress --title="Downloading File..." --auto-close --auto-kill
```

Make it executable:
```

chmod 755 ~/bin/wget_progress_meter.sh
```

Run it like this

```
wget_progress_meter.sh http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list
```

The zenity window will flash up and close pretty quickly because the download is so small.
To see how it really works, download something a bit larger:

```
wget_progress_meter.sh http://archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kdesdk_4.2.2.orig.tar.gz
```

(kdeskd is a 5MB download.)

---

### Post by monsterstack on 2009-06-01
> **unutbu said:**
> This command comes from Twigman: [http://ubuntuforums.org/showpost.php?p=1850902&postcount=2:](http://ubuntuforums.org/showpost.php?p=1850902&postcount=2:)


Save this as ~/bin/wget_progress_meter.sh (or whatever you prefer):

```
#!/bin/sh
# Thanks to Twigman: http://ubuntuforums.org/showpost.php?p=1850902&postcount=2
wget "$@" 2>&1 | sed -u 's/.*\ \([0-9]\+\)%\ \+\(.*\)$/\1\n#Downloading \2/' | zenity --progress --title="Downloading File..." --auto-close --auto-kill
```

Make it executable:
```

chmod 755 ~/bin/wget_progress_meter.sh
```

Run it like this

```
wget_progress_meter.sh http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list
```

The zenity window will flash up and close pretty quickly because the download is so small.
To see how it really works, download something a bit larger:

```
wget_progress_meter.sh http://archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kdesdk_4.2.2.orig.tar.gz
```

(kdeskd is a 5MB download.)

Perfect! That's just what I needed. Clever use of sed, I must say. I wonder if I can do something similar for the apt-get part of the script.

---

### Post by 5ive on 2010-11-04
```
sudo apt-get install pidgin 2>&1 | sed -u 's/\ \([0-9]\+\)%.*$/\1/' | zenity --progress
```
Is not progress ;/

---

