---
title: "Handling application/ms-tnef attachment in Evolution"
date: 2006-09-12
forum: Desktop Environments
---

### Post by freedman on 2006-09-12
Hi, 

- When I get sent an attachment of type .doc(ms) the attachment arrives wrapped in the form of attachment.dat in evolution.

- I installed ytnef, & the libytnef0 it requires, which works at the command line to unpackage these wrapped microsoft atachments into their native format eg ytnef -f . application.dat yields the myword.doc contained inside perfectly.

BUT
- I wish to perferably be able to open these .dat packages directly from within Evolution, or

- I wish to at least create a script or launcher or whatever to just associate with .dat to immediately convert the file.

I HAVE TRIED:

 - to create a launcher icon but connot seem to pass the file parameter to ytnef successfully 

 - to create a .sh script & made it executable by chmod u+x viewdat.sh

#!/bin/bash
ytnef -f . $1

but what works in a terminal does not seem to work by association on the Desktop...and my script does not work ?

---

### Post by freedman on 2006-09-13
...well I have made some progress based on trial and error ...
First I got a desktop launcher working on the Desktop which I called ms-tnef which executes the following command: 
ytnef -f /home/andrew/Desktop %0

Now if I save the offensive ms-tnef filetype attachment.dat to the Desktop and drag and drop it on the launcher - voila! It drops the encapsulated ms document on the Desktop for me. I changed over to use the absolute path (yug) but it always works.

Then I tried the script approach which now works in terminal:

#!/bin/bash
ytnef -f /home/andrew/Desktop $1
echo $1

and saved it as viewdat.sh in a ~/scripts directory 
and made it executable with chmod u+x viewdat.sh

so: sh viewdat attachment.dat kindly drops the encapsulated ms document on the Desktop...

Now if anybody can please tell me how to get it to work inside Evolution I would be most appreciative?

---

### Post by butonic on 2006-12-13
maybe this works: [http://mail.gnome.org/archives/evolution-list/2006-February/msg00126.html]("http://mail.gnome.org/archives/evolution-list/2006-February/msg00126.html")?

---

### Post by butonic on 2006-12-13
**optional:** install build environment
```
sudo apt-get install build-essential
```

**optional:** install needed dev-libraries and dependencies:
```
sudo apt-get install libgnome2-dev libgnomeui-dev libgtk2.0-dev evolution-dev ytnef
```

**required:** download, unpack, patch, configure, make and install
```
mkdir -p ~/tmp/src
cd ~/tmp/src
wget http://www.users.on.net/~notzed/src/tnef-plugin-0.0.0.tar.gz
tar -xvzf tnef-plugin-0.0.0.tar.gz
cd tnef-plugin-0.0.0
sed "s/evolution-plugin-2.4/evolution-plugin-2.8/" -i.org configure
./configure && make && sudo make install
```

**works** (maybe you need to restart evolution - the plugin is activated automatically) :)

---

### Post by mr_skater99 on 2006-12-17
sup,

butonic followed your instructions (all dependencies you listed installed fine) and it fails on the ./configure with the following:

configure: error: Library requirements (libgnome-2.0 >= 2.7.0    libgnomeui-2.0 >= 2.7.0    gtk+-2.0 >= 2.4.0    evolution-plugin-2.8 >= 2.3.1 ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Any help or suggestions?

Cheers

---

### Post by fheinsen on 2007-02-22
Once you have installed ytnef, you can set things up to extract attachments from any "winmail.dat" file with right-clicking, by doing the following:[LIST]
[*]Right-click on your desktop wallpaper and click on "Scripts" -> "Open Scripts Folder"; this will open a folder called "nautilus-scripts".
[*]When the folder opens, click on "File" -> "Create New Document" -> "Empty File" and name the new file "Extract winmail.dat attachment(s)"
[*]Right-click on the file and click on "Open"; when the pop-up message appears, click on "Display"; this will open the file with the text editor
[*]Type the following into the text editor:[/LIST]```
#!/bin/bash
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
  if [ -f "$file" ]; then
    cd `dirname $file`
    ytnef -f . $file
  fi
done
```[LIST]
[*]Save and close the file.
[*]Make the file executable -- right-click on it, click on "Properties" and then on the "Permissions" tab, and then select "allow executing file as program."[/LIST]Once you do this, you can right-click on any winmail.dat file and choose "Scripts" -> "Extract winmail.dat attachment(s)" to extract the attachments inside.

Hope this is helpful

---

### Post by ginestre on 2007-05-24
I tried to follow the instructions above, but after screens full of stuff, got the following

checking for libgnome-2.0 >= 2.7.0    libgnomeui-2.0 >= 2.7.0    gtk+-2.0 >= 2.4.0    evolution-plugin-2.8 >= 2.3.1 ... Package evolution-plugin-2.8 was not found in the pkg-config search path. Perhaps you should add the directory containing `evolution-plugin-2.8.pc' to the PKG_CONFIG_PATH environment variable No package 'evolution-plugin-2.8' found
configure: error: Library requirements (libgnome-2.0 >= 2.7.0    libgnomeui-2.0 >= 2.7.0    gtk+-2.0 >= 2.4.0    evolution-plugin-2.8 >= 2.3.1 ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
richard@Richard-upstairs:~/tmp/src/tnef-plugin-0.0.0$ 
richard@Richard-upstairs:~/tmp/src/tnef-plugin-0.0.0$ 

and couldn't open the attcahments. Where did I go wrong?

---

### Post by midgemiles on 2007-11-21
Last post in this thread was May 07, and it is now Nov 07.   I have just followed Butonic's instructions above 13th Dec 2006.  With trial and error it worked.  The missing information for me (with a standard Ubuntu 7.10 installation) was as follows:-

I needed to use the synaptic package manager to install
> the GNU C++ compiler G++
> the "dev" versions of libgnome-2.0, libgnomeui-2.0, 

After that Butonic's last command <./configure && make && sudo make install> ran to completion without a hitch.  I think the other packages not found (gtk+ and evolution-plugins) before installing the dev versions of libgnome and libgnomeui were found once these were installed (there are no "dev" versions of gtk+ and evolution-plugins)

In Butonic's line <sed "s/evolution-plugin-2.4/evolution-plugin-2.8/" -i.org configure"> I had to substitute "2.10" for my current version of evolution (in the "about" dialog box under "Help" in Evolution) instead of "2.8".

Error messages resulting after Butonic's command <./configure && make && sudo make install> about packages not found and suggestions about adding a path to the PKG_CONFIG_PATH environment variable were "red herrings",  as several posts in linux community said it was really due to the "dev" packages not being installed.  I didn't need to find out about changing the PKG_CONFIG_PATH environment variable.

So in conclusion, before following Butonics series of commands, make sure you have the GNU C++ compiler installed, and the "dev" versions of libgnome and libgnomeui installed.
Substitute the version number of evolution you currently have instead of "2.8".

I am only new to the world of linux and don't understand much outside of what I need to understand to get things to work.   Some one else might find I have left something out of my explanation above.   Looking forward to the TNEF plugin coming as standard with evolution!!!

---

