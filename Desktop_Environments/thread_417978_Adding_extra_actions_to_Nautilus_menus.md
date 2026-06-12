---
title: "Adding extra actions to Nautilus menus"
date: 2007-04-22
forum: Desktop Environments
---

### Post by tonywhelan on 2007-04-22
[SIZE="2"][COLOR="Black"]If you install Nautilus Actions, you can add items to the Nautilus menu (both the right-click menus and the main menu). Use System/Administration/Synaptic Package Manager to install 'nautilus-actions' and you'll find it is added to the System/Preferences menu.

When you launch Nautilus Actions Configuration from the System/Preferences menu, you can Add a new action to be available in Nautilus. You can specify that it appears only when a file is selected, or only a folder, or both. You can also specify if it will appear when mutliple items are selected.

For example, as I use Thunderbird email rather than Evolution, I wanted to add a right-click menu action that allowed me to email the file I had selected in Nautilus.

For this example, the Label could be called something like **Email file**, the Path is **mozilla-thunderbird ** and the Parameter to pass is** -compose 'attachment=file://%f'**

In the Conditions tab I select "only files" and I uncheck the box called "Appears if selection has multiple files.." because unfortunately Thunderbird (1.5) will only accept a single attachment from the command line interface. Yep, you can't have multiple attachments this way (maybe TB2 will be different?)

Once the action has been created, restart Nautilus - in a terminal session, type ```
killall nautilus
```

In a Nautilus window, highlight a file and then right-click - you should see the **Email file** item on the menu. It should also appear on the main Edit menu.

You can also run scripts from this Nautilus Actions facility. One thing I miss on the Nautilus menu is the ability to select one or more files and then click on a menu that allows me to copy or move them to a folder I select. Windows Explorer has this facility as buttons on the toolbar.

So I decided to add these options in to Nautilus.

As root, I created a file called **/usr/bin/nautilus_copy_to** and made it executable. I then edited it to contain the script I need to do the work, and added a Nautilus action to call that script with a parameter of **%M** which passes a list of space-separated items (once for each item selected).

In this case the Conditions tab has "only files" selected as I haven't yet bothered to write the code to process whole folders, and I check the box called "Appears if selection has multiple files.." as I want to be able to copy multiple files at once.

The nautilus_move_to file is almost identical but with a minor change to code to accomplish moves rather than copies.

Both will prompt you for a decision before over-writing an existing file.

Below is the code in the nautilus-copy_to file., for information. (edit: And also the MoveTo script.)

**DISCLAIMER: I am a novice script programmer and I don't pretend this code is perfect. It could doubtless be optimised for speed too. If you use this code and your computer self-destructs, your vegetables wilt, your sex life stops or the Antarctic ice-shelves break off, don't complain to me. It's at your own risk.**

```

#! /bin/sh
# nautilus_copy_to
##########################################################################
# Shellscript:	Add CopyTo function to Nautilus
# Version    :  1.01
# Author     :	Tony Whelan
# Date       :	2007-04-24
# Category   :	File Utilities
##########################################################################
# Description
# Provide (via Nautilus Actions Configuration) a right-click menu option
# to Copy selected files to another location via a file dialog
# For simplicity, this version only allows copying files, not folders
##########################################################################
# This version improves the extraction of filename from pathname
# and adds quotes around $i for correct processing of filenames containing spaces
# Note that this script will not copy files from remote machines (SMB)
# The Nautilus Actions Confuguration tool should only allow local files to present this script
#

# Define variables
PN="Nautilus CopyTo"			# program name
VER='1.01'
errmsg1="Sorry, this script requires one or more file names as input parameter(s)."
errmsg2="Script is designed to be called from a Nautilus right-click menu item."
errmsg3=" files were unable to be written to the destination."
copied=0	# Count of files copied
skipped=0	# Count of files skipped 
dest=""		# destination pathname
errcount=0	# count of any errors returned by copy operation
curfile=""	# name of file currently being processed (without path)
s_size=""       # file size of source file
s_date=""       # date/time stamp of source file
t_size=""       # file size of target file
t_date=""       # date/time stamp of target file

###############################
# Define subroutines

# Display usage message and exit script when user presses OK
Usage () {
zenity --error --title "$PN $VER" --text "$errmsg1 $errmsg2"
    exit 1      # return code of 1 signifies script failed to complete action
}

# Display supplied message text (one parameter) and return on press of OK button
msg () {
zenity --info --title "$PN $VER" --text "$1"
}

# Display message showing target filename, and size/datestamps, and prompt to over-write 
okwrite (){
# On return, the $? variable is 0 if you press Ok and 1 if you press Cancel.
response=`zenity --warning --title "$PN $VER - File Exists" --text "File: $1\nFile with same name already exists at destination.\n\nExisting file:\n $2 bytes last changed $3\n\nOverwrite with:\n $4 bytes last changed $5\n\nDo you want to overwrite the file? \n(OK to overwrite, Cancel to skip)"`
}


###############################

# If no parameters supplied, display usage message and exit
[ $# -lt 1 ] && Usage

# Display the CopyTo dialog box for user to select destination
# Note the single quotes in first code line below are backwards single quotes!
# These redirect standard output to the environment variable 'dest'
dest=`zenity --file-selection --directory --title "Select the folder to copy files to"`

# if variable returned is not a valid folder name, user made no selection so abort
[ ! -d "$dest" ]  && exit 1

# Process the parameters

for i
do
    # Get the filename without the path
    # use double quotes around $i to handle filenames with spaces
    curfile=`basename "$i"`

    # Does the file exist at the destination?
    if [ -f "$dest/$curfile" ] # if exist
    then
       # get current source file's size and date/time details   
       s_date=`find "$i" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       s_size=`find "$i" -printf "%s"`
       # get destination file size and date/time details
       t_date=`find "$dest/$curfile" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       t_size=`find "$dest/$curfile" -printf "%s"`
       # prompt user whether to overwrite target with source
       okwrite "$curfile" "$t_size" "$t_date" "$s_size" "$s_date"
      
       if test `expr $?` -gt 0
       then
         skipped=`expr $skipped + 1`
         continue
       fi
    fi
    # copy the file preserving the source file's attributes where possible

    if cp -p "$i" "$dest/$curfile"
    then
	copied=`expr $copied + 1`
    else
	errcount=`expr $errcount + 1`
	msg "Sorry, unable to copy $curfile to ${dest}. You may not have write-access to that folder, or you may be trying to copy from a remote machine"
    fi   
    
done

# Return summary of actions to user
if test `expr $errcount` -gt 0
then
   msg "\nYou copied $copied files and skipped $skipped files. \n\n$errcount $errmsg3"
else
   msg "\nYou copied $copied files and skipped $skipped files."
fi
exit 0



```[/COLOR][/SIZE]

And here's the code for the Move To script:
```

#! /bin/sh
# nautilus_move_to
##########################################################################
# Shellscript:	Add MoveTo function to Nautilus
# Version    :  1.01
# Author     :	Tony Whelan
# Date       :	2007-04-24
# Category   :	File Utilities
##########################################################################
# Description
# Provide (via Nautilus Actions Configuration) a right-click menu option
# to Move selected files to another location via a file dialog
# For simplicity, this version only allows moving files, not folders
##########################################################################
# This version improves the extraction of filename from pathname
# and adds quotes around $i for correct processing of filenames containing spaces
# Note that this script will not copy files from remote machines (SMB)
# The Nautilus Actions Confuguration tool should only allow local files to present this script
#

# Define variables
PN="Nautilus MoveTo"			# program name
VER='1.01'
errmsg1="Sorry, this script requires one or more file names as input parameter(s)."
errmsg2="Script is designed to be called from a Nautilus right-click menu item."
errmsg3=" files were unable to be written to the destination."
copied=0	# Count of files moved
skipped=0	# Count of files skipped 
dest=""		# destination pathname
errcount=0	# count of any errors returned by copy operation
curfile=""	# name of file currently being processed (without path)
s_size=""       # file size of source file
s_date=""       # date/time stamp of source file
t_size=""       # file size of target file
t_date=""       # date/time stamp of target file

###############################
# Define subroutines

# Display usage message and exit script when user presses OK
Usage () {
zenity --error --title "$PN $VER" --text "$errmsg1 $errmsg2"
    exit 1      # return code of 1 signifies script failed to complete action
}

# Display supplied message text (one parameter) and return on press of OK button
msg () {
zenity --info --title "$PN $VER" --text "$1"
}

# Display message showing target filename, and size/datestamps, and prompt to over-write 
okwrite (){
# On return, the $? variable is 0 if you press Ok and 1 if you press Cancel.
response=`zenity --warning --title "$PN $VER - File Exists" --text "File: $1\nFile with same name already exists at destination.\n\nExisting file:\n $2 bytes last changed $3\n\nOverwrite with:\n $4 bytes last changed $5\n\nDo you want to overwrite the file? \n(OK to overwrite, Cancel to skip)"`
}

###############################

# If no parameters supplied, display usage message and exit
[ $# -lt 1 ] && Usage

# Display the MoveTo dialog box for user to select destination
# Note the single quotes in first code line below are backwards single quotes!
# These redirect standard output to the environment variable 'dest'
dest=`zenity --file-selection --directory --title "Select the folder to copy files to"`

# if variable returned is not a valid folder name, user made no selection so abort
[ ! -d "$dest" ]  && exit 1

# Process the parameters

for i
do
    # Get the filename without the path
    # use double quotes around $i to handle filenames with spaces
    curfile=`basename "$i"`

    # Does the file exist at the destination?
    if [ -f "$dest/$curfile" ] # if exist
    then
       # get current source file's size and date/time details   
       s_date=`find "$i" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       s_size=`find "$i" -printf "%s"`
       t_date=`find "$dest/$curfile" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       t_size=`find "$dest/$curfile" -printf "%s"`
       # prompt user whether to overwrite target with source
       okwrite "$curfile" "$t_size" "$t_date" "$s_size" "$s_date"
      
       if test `expr $?` -gt 0
       then
         skipped=`expr $skipped + 1`
         continue
       fi
    fi
    # move the file preserving the source file's attributes where possible
    if mv "$i" "$dest/$curfile"
    then
	copied=`expr $copied + 1`
    else
	errcount=`expr $errcount + 1`
	msg "Sorry, unable to move $curfile to ${dest}. You may not have write-access to that folder, or you may be trying to copy from a remote machine"
    fi   
    
done

# Return summary of actions to user
if test `expr $errcount` -gt 0
then
   msg "\nYou moved $copied files and skipped $skipped files. \n\n$errcount $errmsg3"
else
   msg "\nYou moved $copied files and skipped $skipped files."
fi
exit 0



```

---

### Post by tacubuntuforums on 2007-04-23
Great Tony!
I'm glad to hear that Nautilus features can be extended and that people like you try to improve this application, because it's the one I like less.

The file browser, together with the web browsers, must be the application that is used more in a GUI. So, in my opinion it's crucial for the public acceptance of the system.

Nautilus has adopted some design decisions which are terrible, in my opinion. I won't talk now about the graphic design matters, like the super-big/super-empty menu bars, that occupy a lot of useless space; the big icons on it, etc.
One of the most annoying things I come across every single day is the way file paths are presented. I need, always need,  a Locations Bar which is:

a) Text based, not with buttons. So that you can copy/paste locations from and to it whenever you want; in so many moments and for so many reasons that the program designer can't foresee them.
b) The text location bar should always be present (not with a  Go to.. menu)
c) It should operate not only to go to places but to show always the location of the files you are viewing
d) It should appear also when nautilus is called by a third program when you want to "save as..." a file. So that you can paste directly and quickly the location of the folder where you want to save it and not to go step by step deep inside the tree and forest of the filesystems.

I can't live and I can't feel at ease without it.

This is one of the great mysteries for me in the gnome world: How on earth the people that work in Gnome, who develop Gnome, can live without a Location Bar like the one in Windows Explorer.

Leaving the amount of software and those things  aside, in my opinion, lthe main thing that can make windows more comfortable for a normal user is it's explorer. Nautilus bears no comparison.

Thank you

---

### Post by ComplexNumber on 2007-04-23
**tonywhelan**
thankyou for that HOWTO :). i really should make more use of nautilus actions, but i haven't...yet.


> > **tacubuntuforums said:**
> Great Tony!
I'm glad to hear that Nautilus features can be extended and that people like you try to improve this application, because it's the one I like less.

The file browser, together with the web browsers, must be the application that is used more in a GUI. So, in my opinion it's crucial for the public acceptance of the system.

Nautilus has adopted some design decisions which are terrible, in my opinion. I won't talk now about the graphic design matters, like the super-big/super-empty menu bars, that occupy a lot of useless space; the big icons on it, etc.
One of the most annoying things I come across every single day is the way file paths are presented. I need, always need, a Locations Bar which is:

a) Text based, not with buttons. So that you can copy/paste locations from and to it whenever you want; in so many moments and for so many reasons that the program designer can't foresee them.
b) The text location bar should always be present (not with a  Go to.. menu)
c) It should operate not only to go to places but to show always the location of the files you are viewing
d) It should appear also when nautilus is called by a third program when you want to "save as..." a file. So that you can paste directly and quickly the location of the folder where you want to save it and not to go step by step deep inside the tree and forest of the filesystems.

I can't live and I can't feel at ease without it.

This is one of the great mysteries for me in the gnome world: How on earth the people that work in Gnome, who develop Gnome, can live without a Location Bar like the one in Windows Explorer.

Leaving the amount of software and those things aside, in my opinion, lthe main thing that can make windows more comfortable for a normal user is it's explorer. Nautilus bears no comparison.

Thank you
is this what you are talking about (see screenshot)?

hmmm it looks like you'll have to spend a few more minutes with nautilus before you end up coming to any more wrong conclusions.

---

### Post by tonywhelan on 2007-04-23
> **tonywhelan said:**
> 
You can also run scripts from this Nautilus Actions facility. One thing I miss on the Nautilus menu is the ability to select one or more files and then click on a menu that allows me to copy or move them to a folder I select. Windows Explorer has this facility as buttons on the toolbar.

So I decided to add these options in to Nautilus.


I should note that I have made a minor edit to the code for the "Copy To" script above to fix a problem with filenames that contain spaces.. In case anyone had taken a copy of the original script.

---

### Post by tonywhelan on 2007-04-23
> **tacubuntuforums said:**
> 
One of the most annoying things I come across every single day is the way file paths are presented. I need, always need,  a Locations Bar which is:

a) Text based, not with buttons. So that you can copy/paste locations from and to it whenever you want; in so many moments and for so many reasons that the program designer can't foresee them.
b) The text location bar should always be present (not with a  Go to.. menu)
c) It should operate not only to go to places but to show always the location of the files you are viewing
d) It should appear also when nautilus is called by a third program when you want to "save as..." a file. So that you can paste directly and quickly the location of the folder where you want to save it and not to go step by step deep inside the tree and forest of the filesystems.


Hello tacubuntuforums

Re your list above:
The Location bar can display text rather than buttons. Click on the left-most button and it toggles between button mode and text mode. This is "sticky", ie it remembers your last setting and stays that way unless you toggle back. It should always show you the folder location of the files you are looking at. (I wasn't even aware of the GoTo feature till you mentioned it)

Do you have the Side Pane enabled (View menu). It allows you to toggle between a Places list (that you can add to like favourites), or a Tree view of the system, plus a couple of other views I don't use. You can navigate quicker with that.

In the Save As dialog box presented by Nautilus when called by programs such as Text Editor, you can past a path into the Name field and then just type the filename you want to call it, rather than drilling down through folders.

Unless I have misunderstood what you were saying above, I think the features you mention are mostly present. 

There are a few things that are annoying to me. One is the fact that if you want to paste a file from clipboard into a window, you can't do it  (unless you have a folder selected) via a right-click Paste or a toolbar button, only via the Edit menu. But if you have the Side Pane in Tree view mode, you can paste into the desired folder in the Side Pane. I think it's a case of getting accustomed to how to make Nautilus do what you want. 


cheers

Tony

---

### Post by sawjew on 2007-10-16
Tony, I love your additions to Nautilus and I thought I would share some minor modifications I made to your scripts.  I added a graphical progress indicator to show how your copy is progressing.  This is only really useful when copying large files and nothing takes as long to copy in linux as in Windows anyway.  I also added an option to open the destination directory and I changed the dialog when it asks if you want to replace the existing file.  As it was it said to click OK to replace and Cancel to not replace but there was no Cancel button, so I just changed it from an info to a question  dialog to include the Cancel button.  I have pasted the changed scripts below.

The Copy to script;
```
#! /bin/sh
# nautilus_copy_to
##########################################################################
# Shellscript:	Add CopyTo function to Nautilus
# Version    :  1.01
# Author     :	Tony Whelan
# Date       :	2007-04-24
# Category   :	File Utilities
##########################################################################
# Description
# Provide (via Nautilus Actions Configuration) a right-click menu option
# to Copy selected files to another location via a file dialog
# For simplicity, this version only allows copying files, not folders
##########################################################################
# This version improves the extraction of filename from pathname
# and adds quotes around $i for correct processing of filenames containing spaces
# Note that this script will not copy files from remote machines (SMB)
# The Nautilus Actions Confuguration tool should only allow local files to present this script
#

# Define variables
PN="Nautilus CopyTo"			# program name
VER='1.01'
errmsg1="Sorry, this script requires one or more file names as input parameter(s)."
errmsg2="Script is designed to be called from a Nautilus right-click menu item."
errmsg3=" files were unable to be written to the destination."
copied=0	# Count of files copied
skipped=0	# Count of files skipped 
dest=""		# destination pathname
errcount=0	# count of any errors returned by copy operation
curfile=""	# name of file currently being processed (without path)
s_size=""       # file size of source file
s_date=""       # date/time stamp of source file
t_size=""       # file size of target file
t_date=""       # date/time stamp of target file

###############################
# Define subroutines

# Display usage message and exit script when user presses OK
Usage () {
zenity --error --title "$PN $VER" --text "$errmsg1 $errmsg2"
    exit 1      # return code of 1 signifies script failed to complete action
}

# Display supplied message text (one parameter) and return on press of OK button
msg () {
zenity --question --title "$PN $VER" --text "$1"
}

# Display message showing target filename, and size/datestamps, and prompt to over-write 
okwrite (){
# On return, the $? variable is 0 if you press Ok and 1 if you press Cancel.
response=`zenity --question --title "$PN $VER - File Exists" --text "File: $1\nFile with same name already exists at destination.\n\nExisting file:\n $2 bytes last changed $3\n\nOverwrite with:\n $4 bytes last changed $5\n\nDo you want to overwrite the file? \n(OK to overwrite, Cancel to skip)"`
}


###############################

# If no parameters supplied, display usage message and exit
[ $# -lt 1 ] && Usage

# Display the CopyTo dialog box for user to select destination
# Note the single quotes in first code line below are backwards single quotes!
# These redirect standard output to the environment variable 'dest'
dest=`zenity --file-selection --directory --title "Select the folder to copy files to"`

# if variable returned is not a valid folder name, user made no selection so abort
[ ! -d "$dest" ]  && exit 1

# Process the parameters

for i
do
    # Get the filename without the path
    # use double quotes around $i to handle filenames with spaces
    curfile=`basename "$i"`

    # Does the file exist at the destination?
    if [ -f "$dest/$curfile" ] # if exist
    then
       # get current source file's size and date/time details   
       s_date=`find "$i" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       s_size=`find "$i" -printf "%s"`
       # get destination file size and date/time details
       t_date=`find "$dest/$curfile" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       t_size=`find "$dest/$curfile" -printf "%s"`
       # prompt user whether to overwrite target with source
       okwrite "$curfile" "$t_size" "$t_date" "$s_size" "$s_date"
      
       if test `expr $?` -gt 0
       then
         skipped=`expr $skipped + 1`
         continue
       fi
    fi
    # copy the file preserving the source file's attributes where possible

    if cp -p "$i" "$dest/$curfile" | zenity --progress --pulsate --title "Please Wait" --text "Copying $curfile"
    then
	copied=`expr $copied + 1`
    else
	errcount=`expr $errcount + 1`
	msg "Sorry, unable to copy $curfile to ${dest}. You may not have write-access to that folder, or you may be trying to copy from a remote machine"
    fi   
    
done

# Return summary of actions to user
if test `expr $errcount` -gt 0
then
   msg "\nYou copied $copied files and skipped $skipped files. \n\n$errcount $errmsg3"
else
  zenity --question --title="Copy Complete" --text="\nYou copied $copied files and skipped $skipped files. Would you like to open the destination directory?"
   case "$?" in
	1  )  exit 1 ;;
	0  )  nautilus "$dest" ;;
   esac
fi
exit 0
```

The Move to script;
```
#! /bin/sh
# nautilus_move_to
##########################################################################
# Shellscript:	Add MoveTo function to Nautilus
# Version    :  1.01
# Author     :	Tony Whelan
# Date       :	2007-04-24
# Category   :	File Utilities
##########################################################################
# Description
# Provide (via Nautilus Actions Configuration) a right-click menu option
# to Move selected files to another location via a file dialog
# For simplicity, this version only allows moving files, not folders
##########################################################################
# This version improves the extraction of filename from pathname
# and adds quotes around $i for correct processing of filenames containing spaces
# Note that this script will not copy files from remote machines (SMB)
# The Nautilus Actions Confuguration tool should only allow local files to present this script
#

# Define variables
PN="Nautilus MoveTo"			# program name
VER='1.01'
errmsg1="Sorry, this script requires one or more file names as input parameter(s)."
errmsg2="Script is designed to be called from a Nautilus right-click menu item."
errmsg3=" files were unable to be written to the destination."
copied=0	# Count of files moved
skipped=0	# Count of files skipped 
dest=""		# destination pathname
errcount=0	# count of any errors returned by copy operation
curfile=""	# name of file currently being processed (without path)
s_size=""       # file size of source file
s_date=""       # date/time stamp of source file
t_size=""       # file size of target file
t_date=""       # date/time stamp of target file

###############################
# Define subroutines

# Display usage message and exit script when user presses OK
Usage () {
zenity --error --title "$PN $VER" --text "$errmsg1 $errmsg2"
    exit 1      # return code of 1 signifies script failed to complete action
}

# Display supplied message text (one parameter) and return on press of OK button
msg () {
zenity --info --title "$PN $VER" --text "$1"
}

# Display message showing target filename, and size/datestamps, and prompt to over-write 
okwrite (){
# On return, the $? variable is 0 if you press Ok and 1 if you press Cancel.
response=`zenity --warning --title "$PN $VER - File Exists" --text "File: $1\nFile with same name already exists at destination.\n\nExisting file:\n $2 bytes last changed $3\n\nOverwrite with:\n $4 bytes last changed $5\n\nDo you want to overwrite the file? \n(OK to overwrite, Cancel to skip)"`
}

###############################

# If no parameters supplied, display usage message and exit
[ $# -lt 1 ] && Usage

# Display the MoveTo dialog box for user to select destination
# Note the single quotes in first code line below are backwards single quotes!
# These redirect standard output to the environment variable 'dest'
dest=`zenity --file-selection --directory --title "Select the folder to copy files to"`

# if variable returned is not a valid folder name, user made no selection so abort
[ ! -d "$dest" ]  && exit 1

# Process the parameters

for i
do
    # Get the filename without the path
    # use double quotes around $i to handle filenames with spaces
    curfile=`basename "$i"`

    # Does the file exist at the destination?
    if [ -f "$dest/$curfile" ] # if exist
    then
       # get current source file's size and date/time details   
       s_date=`find "$i" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       s_size=`find "$i" -printf "%s"`
       t_date=`find "$dest/$curfile" -printf "%Ta %Td %Tb %TY %TH:%TM:%TS"`
       t_size=`find "$dest/$curfile" -printf "%s"`
       # prompt user whether to overwrite target with source
       okwrite "$curfile" "$t_size" "$t_date" "$s_size" "$s_date"
      
       if test `expr $?` -gt 0
       then
         skipped=`expr $skipped + 1`
         continue
       fi
    fi
    # move the file preserving the source file's attributes where possible
    if mv "$i" "$dest/$curfile" | zenity --progress --pulsate --title "Please Wait" --text "Moving $curfile"
    then
	copied=`expr $copied + 1`
    else
	errcount=`expr $errcount + 1`
	msg "Sorry, unable to move $curfile to ${dest}. You may not have write-access to that folder, or you may be trying to copy from a remote machine"
    fi   
    
done

# Return summary of actions to user
if test `expr $errcount` -gt 0
then
   msg "\nYou moved $copied files and skipped $skipped files. \n\n$errcount $errmsg3"
else
   zenity --question --title="Move Complete" --text="\nYou moved $copied files and skipped $skipped files. Would you like to open the destination directory?"
   case "$?" in
	1  )  exit 1 ;;
	0  )  nautilus "$dest" ;;
   esac
fi
exit 0
```

By the way you should put this up on the Nautilus Actions website for other people to use.  If you don't wish to I cold place it up there when I have time.

Thanks once again for your work.

---

### Post by tonywhelan on 2007-10-16
Thanks for the feedback and the improvements. I'm just now rebuilding a machine with GG (release candidate, I couldn't wait) and will try the modified scripts there shortly. 

When you refer to the Nautilus Actions website, is that [http://www.grumz.net](http://www.grumz.net) ?
I'll have a look at that today in between all the other things on my to-do list ...

---

### Post by sawjew on 2007-10-16
Yes I was referring to the Grumz web site particularly this page [http://www.grumz.net/index.php?q=configlist]("http://www.grumz.net/index.php?q=configlist")

I know the feeling, I upgraded to Gutsy a couple of weeks ago.  The only hassles I've had have been with sound and DVD playing.  Other than that it's been improvements all around.

Have fun!!  I'd better get back to work now.

---

### Post by tonywhelan on 2007-10-17
I have had a play with the modified script. Your addition of an option to open the destination folder at end of copy/move is a good idea. 

I am rewriting the scripts to put the test for writeability of the destination folder right up front, rather than on a per-files basis, so if you try to copy 25 files to a folder to which you don't have write permissions, you'll get prompted once only, not 25 times, and be invited to choose another folder instead.

The Progress Bar dialog causes a problem insofar as it stops the detection of a cp (copy) failure. Failures could happen if for example you try to copy from an SMB window in Nautilus. The Nautilus Actions Config should be set to prevent the scripts being displayed for SMB files but if someone changes that setting then it's desirable to report that the copy action has failed. If I can see a way to check success or failure and include a progress bar at same time, I'll do it. 

Once I have finished rewriting the scripts I'll post them here and also put a config on the Grumz site.

---

### Post by tonywhelan on 2007-10-17
I just found some posts from 2005 that use a rather smaller script to do much the same. First see [https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts) for a simple non-recursive script. 

Then see [http://ubuntuforums.org/archive/index.php/t-101859.html](http://ubuntuforums.org/archive/index.php/t-101859.html) for a recursive version of the script (though there is an error in the script that I have commented on re how to fix).

I have to say that KDE's Konqueror is starting to appeal to me - it has Move To/Copy To, split windows, customisable toolbars and above all Undo/Redo. And KDE's desktop search handles imap local folders on thunderbird & evolution (whereas Gnome Tracker only does Evo. 

I just find it a bit hard to contemplate making the move to a new GUI ....

---

### Post by sawjew on 2007-10-17
Tony, I tried those script before I found yours and they work great as scripts but will not work correctly when used with Nautilus Actions.  I think the problem  is that the copy part of the script needs the full path but the conflict check needs the file name only.  I could it working to check for conflicts or to copy the file with no conflict check but not both.  If I set the parameter as %M it would copy but not check for conflicts and if I set it for %f (I think that was what I used) then it would check for conflicts, say it had copied but would not actually perform the copy.  I think it is a little too simplistic for using with nautilus actions.

By the way do you realise that Konqueror is being replaced in KDE with Dolphin which is a much simpler file manager.  My biggest complaint with KDE is how integrated konqueror is in the desktop, much like explorer is in Windows, and it is very difficult to use anything different.  Why I really like Gnome is that it doesn't have everything including the kitchen sink but it is reasonably easy to add anything you want such as these nautilus extensions.  

I also think KDE looks like a cheap plastic toy with graphics designed by a 3 year old but I won't get into a discussion about the merits of DEs here.

---

### Post by tonywhelan on 2007-10-19
Hi sawjew

When I said Konqueror I actually meant the Dolphin file manager, sorry for the confusion. I agree with you about konqueror and the kitchen sink. I tried a Kubuntu 7.10 install on a spare disk and the menus had too much clutter for my liking. But the main issue was that lots of things I tried to do caused a KDE crash. Put me right off it.

I have Ubuntu 7.10 installed now (should have waited a week, the mirrors were really being hammered yesterday, everything downloaded so slowly). Then I installed Dolphin from the repository. It would need some tweaking as some commands (like Delete) won't work as Gnome uses different conventions. But that can wait.

---

### Post by tonywhelan on 2007-10-19
I want to re-visit my Move/Copy scripts to improve them, especially to allow them to copy/move folders. The issue for me is a suitable means of warning the user about overwriting existing files. The standard warning in Nautilus, Dolphin and Windows is along the lines of "if you copy/move, then files in the target will be overwritten" and I guess that's good enough but I was thinking I might add an option that showed all of the files in a listbox so the user could see what was about to get over-written.

But not this week .....

---

### Post by efilnikufecin on 2008-01-23
Finally!!!  Copying & moving files from one location to another were 2 Windows Explorer functions that I terribly missed.  Good job!!!

---

### Post by tonywhelan on 2008-02-14
> **tonywhelan said:**
> I want to re-visit my Move/Copy scripts to improve them, especially to allow them to copy/move folders. The issue for me is a suitable means of warning the user about overwriting existing files. The standard warning in Nautilus, Dolphin and Windows is along the lines of "if you copy/move, then files in the target will be overwritten" and I guess that's good enough but I was thinking I might add an option that showed all of the files in a listbox so the user could see what was about to get over-written.

But not this week .....

[SIZE="3"]I have just found a set of scripts that do both file and folder copying or moving.

See the NScripts collection by Christopher Bratusek at [http://www.nanolx.org/]("http://www.nanolx.org/")

These scripts do NOT prompt you with a warning if you are about to over-write an existing file/folder, but that could easily be added.

NB if you want to add scripts like this to the Nautilus Actions Configuration (NAC) menu (See System, Preferences), you'll have to use %M as the parameter in NAC, and amend the scripts to replace "$NAUTILUS_SCRIPT_CURRENT_URI" with "$*"

Trying to collect the value of $NAUTILUS_SCRIPT_CURRENT_URI from a script launched via NAC will return a blank, hence you need to use  $* to grab the passed parameter(s) instead.

 [/SIZE]

---

