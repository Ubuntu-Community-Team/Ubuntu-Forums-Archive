---
title: "Nautilus Script send file as attachment using mpack"
date: 2012-10-10
forum: Desktop Environments
---

### Post by filibertov on 2012-10-10
I have installed "mpack" and used it successfully to send an attachment via email using the command line. Like this:

```
mpack -s "tool"  tooling.pdf user@email
```

  I would like to be able to right click on a file, select "Send to", then select one from a list of about 6 recipients, have a pop-up to input subject, and that's it.  The email is sent with the attachment.

Can anyone show me how to do this?  I was trying to use the Nautilus-Actions Configuration Tool but it is too much for me.

Thanks!

---

### Post by Vaphell on 2012-10-12
```
#!/bin/bash

recipients="name1
user1@email
name2
user2@email
name3
user3@email"

while read -r f
do
  # check if file and add to list
  if [ -f "$f" ]; then files+=( "$f" ); fi
done <<< "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

if (( ${#files[@]}==0 ))  # nothing to send = exit
then
  exit
fi

# recipient
r=$( zenity --list --title="Address book" --text="Select recipient" --column=name --column=address --print-column=2 <<< "$recipients" )
# subject
s=$( zenity --entry --title="Subject" --text="Enter subject" )

if (( ${#files[@]}==1 ))  # 1 file
then
  mpack -s "$s" "${files[0]}" "$r"
elif (( ${#files[@]}>1 ))  # multiple files
then
  for(( i=0; i<${#files[@]}; i++ ))
  do
    mpack -s "$s (#$((i+1)))" "${files[$i]}" "$r"
  done
fi
```
in my 10.04 it works when placed in ~/.gnome2/nautilus-scripts (though i didn't bother to check if things get sent, i just printed the commands that were supposed to be executed), requires **zenity** to work

recipients string fills the table with stuff, every cell needs a separate line.

script is longer than necessary because i added test ignoring directories and option of sending multiple files at once. In that scenario script generates separate mails with -s "subject (#1/2/3...)"


the main difference between nautilus-scripts and nautilus-actions is the way data is passed to the script - NA uses ordinary parameters, while NS uses special variable with newline delimited list of filenames. Reworking the script to fit NautilusActions would not be that hard, in fact it should be easy to write a script that figures out how it was called (number of params != 0 => n-actions, non-empty $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable => n-scripts) and do the right thing with input.
NA looks complicated because allows customizing  what exactly gets passed to the script (dir part/name part/full path/...), the conditions for which the option should be available, like single/multiple selection, only files/dirs, certain filetypes etc (which is what pretty much all the tabs in the config tool do).

---

### Post by filibertov on 2012-10-13
Thank you it looks great! I tested it and it freezes right after I select the recipient and click ok.  Then I kill zenity (killall zenity) and the subject box comes up.  I input subject and it closes.

At the moment I can't check if it is actually sending the file.  I will do this Monday but I'd like to find out why it freezes.

I copied your script and pasted.  Any ideas?

---

### Post by Vaphell on 2012-10-14
it appears zenity is broken in 12.04. I launched precise in virtualbox and when i use the code of the first window in terminal and confirm the selection with OK this happens, ad infinitum:
```
(zenity:2561): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/giounix.c:411Error while getting flags for FD: Bad file descriptor (9)


(zenity:2561): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/giounix.c:411Error while getting flags for FD: Bad file descriptor (9)

...
```
lame :/

you can use yad instead, it's a fork of zenity so it works pretty much the same
[http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html](http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html)
```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install yad
```

in the script:
```
r=$( yad --list --title="Address book" --text="Select recipient" --column=name --column=address --separator='' --width=400 --height=300 --print-column=2 <<< "$recipients" )
s=$( yad --entry --title="Subject" --text="Enter subject" )
```
as you can see it's almost the same code.
I added width and height because at least in my case the default size was too small. You can configure window sizes to suit your needs.

---

### Post by filibertov on 2012-10-16
That's strange... I tried the script at home using yad and it worked (using 12.04).  But I just tried it here at work and it doesn't work.  The selection box comes up empty (blank).  I am also using 12.04 at work.

I switched back the script to use zenity and the same freezing error happened after selecting the contact and clicking ok.  Then I killed the process, I got the subject box, entered the subject, clicked ok and I got the email.

Do you have any idea what may be happening?  Except for replacing the names and actual email addresses and changing the zenity script for the yad command, everything else is identical.

---

### Post by filibertov on 2012-10-18
Copied the script that I used at home into my scripts at work.  Home script works, work script doesn't.

Any ideas.  They are both 12.04 and up to date.

---

### Post by filibertov on 2012-10-22
After testing a bit, this is what ended up working. Making sure there were no spaces in the user's name.  I used and underscore.

```
#!/bin/bash

recipients="John_Hancock johnh@email
user2 user2@email
user3 user3@email"

while read -r f
do
  # check if file and add to list
  if [ -f "$f" ]; then files+=( "$f" ); fi
done <<< "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

if (( ${#files[@]}==0 ))  # nothing to send = exit
then
  exit
fi

# recipient
r=$( yad --list --title="Address book" --text="Select recipient" --column=Name --column=Address  --width=400 --height=300 --separator='' --print-column=2 $recipients )

# subject
s=$( yad --entry --title="Subject" --text="Enter subject" )

if (( ${#files[@]}==1 ))  # 1 file
then
  mpack -s "$s" "${files[0]}" "$r"
elif (( ${#files[@]}>1 ))  # multiple files
then
  for(( i=0; i<${#files[@]}; i++ ))
  do
    mpack -s "$s (#$((i+1)))" "${files[$i]}" "$r"
  done
fi
```

---

