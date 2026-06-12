---
title: "Trouble installing ApE (A plasmid Editor) on Ubuntu 10.04"
date: 2011-02-21
forum: Education &amp; Science
---

### Post by climbe2 on 2011-02-21
Hello all. I am rather new to Linux, and usually only use the command line interface when instructions are provided.  I have had some difficulty installing ApE (A plasmid Editor) on Ubuntu 10.04.  I followed the instructions provided by the program author [[here]]("http://biologylabs.utah.edu/jorgensen/wayned/ape/Download/ApE%20documentation.doc"); I installed tclkit version8.5.1  found [[here]]("http://equi4.com/tclkit/download.html") for my 32bit x86.  after installation of ApE I received the message "There was an error creating the child process for this terminal" when executing via the menu link I created.  I read [this]("http://www.compdigitec.com/labs/2009/05/12/fixing-there-was-an-error-creating-a-child-process-for-this-terminal/") article and thought that I had fixed the terminal error, but to no avail.  I really don't want to run this program on Windows, I'm making steady progress using Linux, and it's fun and exciting as well.  Any suggestions?[URL="http://www.compdigitec.com/labs/2009/05/12/fixing-there-was-an-error-creating-a-child-process-for-this-terminal/"]
[/URL]

---

### Post by rayshao on 2011-02-26
Hi, I wrote a mini tutorial here: [http://ape-a-plasmid-editor.wikispaces.com/message/view/How+do+I+do...%3F/32935290]("http://ape-a-plasmid-editor.wikispaces.com/message/view/How+do+I+do...%3F/32935290")

The instructions are as follows:

1) Go to [http://equi4.com/tclkit/download.html](http://equi4.com/tclkit/download.html) and download the most recent version of Tclkit for Linux that corresponds to your CPU architecture (if you have an Intel, it will probably be "x86 (32b)").

2) Open the downloaded archive and drag-and-drop the file inside onto your desktop. Rename the file to "tclkit".

3) Open a terminal window (for Ubuntu, this is under the menu "Applications" --> "Accessories" --> "Terminal".

4) By default, a new terminal window should open to your user directory. Confirm by typing "ls" and hit ENTER. You should see a list of your folders such as Documents, Downloads, Desktop, etc.

5) Once you have confirmed you are in your user directory, type "cd Desktop" (this is caps-sensitive) and hit ENTER.

6) Type "ls" and hit ENTER to list the files on your Desktop. You should see "tclkit" among them. Type "sudo mv tclkit /usr/bin/" to move the tclkit file to where it needs to go. You will be prompted for your root password, which you should have established when you first installed Ubuntu.

7) Now go to where you've moved tclkit by typing "cd /usr/bin/" and hit ENTER. Type "sudo chmod +x tclkit" and hit ENTER, which will allow tclkit to be run as an executable command. You will again be prompted for your password.

8) Now, go to the ApE website and download the ApE Linux archive. The archive contains both the ApE Linux folder and the Mac OSX folder which you can ignore. Drag and drop the "ApE Linux" folder into a location of your choice. I recommend something easy to find, like on your Desktop or Documents folder. Notice that inside the ApE Linux folder is a file called "AppMain.tcl"; however, you cannot just double click this. Normally you would open it via terminal command. However, you can create a menu shortcut that will make things easier.

9) To create the shortcut, right click the top menu bar and click "Edit Menus". Under the "Science" category (or another if you choose), click "New Item". A new window will come up. Under "Type", select "Application in Terminal". Under "Name", write whatever name you wish. Under "Command", click browse and find where you put AppMain.tcl. Once you select that file, it should display the location of AppMain.tcl, for example "/home/user/Desktop/ApE%Linux/AppMain.tcl" Now, in FRONT of that location type "tclkit ", so that the entire location becomes "tclkit /home/user/Desktop/ApE/AppMain.tcl". Note that there is a single space between "tclkit" and "/home".

10) Click "OK" and that should be it! Go to the new menu item you created under "Applications" and click it. A terminal window should pop up, then ApE should appear! Leave the terminal window open until you are done with ApE; if you close the terminal window it will also close ApE.


Good luck! I am by no means a linux expert, so if anyone wants to pitch in a better way to do this, I would not be offended.

---

### Post by climbe2 on 2011-03-18
Rayshao, thank you for your reply.  I have followed these instructions, and get an error:  Failed to execute child process "tclkit /home/charles/Documents/ApELinux/AppMain.tcl" (No such file or directory). Any suggestions?

---

### Post by rayshao on 2011-04-08
Hi, I wish I could help more, but it is difficult to troubleshoot this over the internet (at least for me, given my limited knowledge of Linux). The only thing I can recommend is that you redo every step to make sure no mistakes were made along the way. For example, is "ApELinux" the correct spelling for the folder that AppMain.tcl is in? Because by default, ApE is supplied in a folder "ApE Linux" with a space, and thus when directing a shortcut to it, you need a percent sign to represent the space, e.g. "ApE%Linux". Or you can just rename the folder (which you might have done) to remove the space. Other than that I don't know what could be wrong.

---

### Post by nebjamin on 2011-07-28
Hi

It's a pitty that APE does not support Linux anymore. I think the best solution would be to run the .exe under Wine.

nebjamin

---

### Post by apf2718 on 2011-11-12
The Windows & Mac releases of ApE are just packaged versions of the TCL script that Wayne used to provide -- with a bit of work, you can get them running under Linux/Unix natively.

I've posted a log of how I did this here:

[http://pastebin.com/fJNjcW1G](http://pastebin.com/fJNjcW1G)

---

