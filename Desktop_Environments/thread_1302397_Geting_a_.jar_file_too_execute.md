---
title: "Geting a *.jar file too execute"
date: 2009-10-27
forum: Desktop Environments
---

### Post by cudayne on 2009-10-27
Hello i am having a small problem. I play a battleteck game called mekwars. the problem is i can not get the *.jar files too execute as a program. I have right clicked on the main folder an even the files within told them to give me read an write privlages too execture as a sun java program an i still get check folder privlages error.

the strange thing is there is a *.sh file that execture the program.

The following is in the *.sh hopefully this helps

mkdir data;

echo UPDATEURL=http\://www.themekwarscollective.org/WoK/Files/Update/> data/mwconfig.txt;

java -jar MekWarsAutoUpdate.jar PLAYER;

I find it strange that this runs the program but double clicking on the *.jar file wont.

oh I am running java 6 an ubuntu 9.04(9.1 runs for 30 min an locks up tight so reverted back too 9.04)

---

### Post by Dark_Stang on 2009-10-27
Right click on the jar file, click properties.
Go to the "Open With" tab.
Select Sun Java 6 Runtime and hit close. 
Double click on the jar file.
Dance to techno music.

---

### Post by cudayne on 2009-10-27
done that still says failed too create config file check folder privlages.

---

### Post by major.stubble on 2009-10-27
> **cudayne said:**
> done that still says failed too create config file check folder privlages.

The issue here is that the application you have downloaded needs to be run within its current directory.  I do not know of a 'gui' way to do this.  (In Windows, this would be the 'Run In' option for a shortcut.)

Here are the steps that I followed to get this application to work:

1) Download the application, then open the zip file in Archive Manager (can be done automatically with Firefox by selecting 'Open' when it has completed download).

2) Drag the enclosed 'WoKClient' to your Desktop.

3) *REQUIRED* Open the WoKClient/WoKClient director. Left click 'File' then 'Create Folder'.  Name this folder "logs".

3) Right mouse click on "MekWarsAutoUpdate.jar" and left mouse click 'Open with "Sun Java 6 Runtime".

This will load the update client and download the application files.

At this point, there is an issue with what the previous poster suggested.  When you set up Java to run this .jar on double click, it will set the working directory to something other than the directory where the "MekWarsClient.jar" exists.  It would be better to create a script file in that directory:

1) Browse to the WoKClient directory by double-clicking the WoKClient folder icon on your Desktop.  This should be:  Username/WoKClient

2) Left click 'File', hover over 'Create Document', then left click 'Empty File'.  Name this file 'run_client.sh' (the only important part is the extention, you can name this anything you want - though I would keep it simple and without spaces).

3) Right click 'run_client.sh' and hover over 'Open With' then left click 'Open with "Text Editor"'.

4) Paste the following code into the text file:

```
#!/bin/sh
cd ~/Desktop/WoKClient/WoKClient
java -jar MekWarsClient.jar
```Save the file and quit Text Editor.

5) Right click 'run_client.sh' and left click 'Properties'.

6) Within the popup, left click the 'Permissions' tab.  Check the 'Allow executing file as program' check box.  Click close.

7) Double click the 'run_client.sh' icon.  A popup will appear asking 'Do you want to run "run_client.sh", or display its contents?'.  Left click the 'Run' button.

This should run the applicaiton without issue.  To add this to your Gnome 'Applications' menu:

1) From the Gnome task bar, left click 'System', hover over 'Preferences', and left click 'Main Menu'.

2) Select the 'Games' category under the 'Menus:' pane.

3) Left click the 'New Item' button.

4) Type "Mek Wars" (or your own prefered name) in the 'Name' text field.

5) Left click the 'Browse' button.  Navigate to the WoKClient folder where the 'run_client.sh' command is located.  Select the 'run_client.sh' file and left click the 'Open' button.

6) Left click the 'Close' button.  Visually verify that 'Mek Wars' shows up in the 'Items:' column and has a check mark next to it.

7) Left click the 'Close' button.

Now you should have a menu entry that will execute the shell script for WoKClient.  Now, if you ever move this folder to somewhere else, make sure that you update both the 'run_client.sh' script as well as the menu item.

Hope that helps.  It is not ideal, so you may want to wait to see if others have better solutions to this problem.

-Major Stubble

---

### Post by cudayne on 2009-10-29
Awsome thank you. although i couold not get the update jar too run i think it had something too do with not knowing the extension for the logs file. I used the direction for makeing the actual game run an it ran the autoupdate perfectly. Thank you.

---

