---
title: "Automatic image uploader?"
date: 2009-06-15
forum: General Help
---

### Post by mike0020 on 2009-06-15
I've come across something called GrabUp ([http://grabup.com/](http://grabup.com/)) for Mac which lets users take a picture using the print screen button and it will automatically upload the image to their site (or ones own site with a paid upgrade) and put the link to the image in the person's clipboard. I was wondering if anyone knows of something like this for Ubuntu.

---

### Post by mike0020 on 2009-06-16
bump

---

### Post by mike0020 on 2009-06-18
Well because I didn't get any results I thought I'd try to write my own script that does this and I was successful.

First, you'll need these two programs:

sudo apt-get install compizconfig-settings-manager
sudo apt-get install xclip

Now make a directory in your home folder called .imageup (you can name it whatever you want however I will be referring to it as .imageup)

Once you have done that download this bash script into your .imageup folder and name it upload.sh:

```
#!/bin/bash

randstring="`< /dev/urandom tr -dc A-Za-z0-9 | head -c32`.png"

HOST="ftp.yoursite.com"
USER="youruser"
PASSWD="yourpass"

IMG="~/.imageup/screenshot"?".png"
echo "http://yoursite.com/images/$randstring" | xclip -selection clipboard

ftp -n $HOST <<EOF
quote USER $USER
quote PASS $PASSWD
cd /images/
put $IMG $randstring
EOF
rm $IMG
```

You'll have to edit your ftp info (5-7), the URL (10), and the directory you're moving to in ftp (15). **Make sure that the directory you're moving to is present otherwise this will not work.** Once you've finished editing everything in the file, open up terminal and run this:

```
chmod +x ~/.imageup/upload.sh
```

Now all you have to do is open up CompizConfig Settings Manager (System > Preferences > CompizConfig Settings Manager) and search for Screenshot then enter this information:

Directory: ~/.imageup/
Launch Application: ~/.imageup/upload.sh

Enable the plugin and you're done. To use it simply hold the super button and drag your left mouse button around where you want to take a screenshot. When you release, the link to your screenshot will be in your clipboard.

I'd like to say thanks to everyone in #ubuntu on freenode who helped me with this.

---

