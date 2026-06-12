---
title: "PCMANFM in Lubuntu"
date: 2014-08-24
forum: Desktop Environments
---

### Post by graylinux on 2014-08-24
Hi

I managed to get my first convert from WinXp to Lubuntu...!!   Sadly, the first thing he wanted to do he was unable to do and I have failed to resolve the problem.

He went into one of his photograph folders in PCMANFM, selected 3 .jpgs, right-clicked.... an... arrgghhh....no option to send via thunderbird (the mail client I set up for him). Now we all know that he could create a mail then attach multiple photos but that's not really the point. I assured him if it could be done in XP it could be done in Lubuntu!.I have now spent days on it! 

I discoved the .desktop feature in PCMANFM (whereby a .desktop can be placed in /home/myusername/.local/share/file-manager/actions) and managed to at least get a custom right-click option working to  'Send via Thunderbird'... but only for a single photo. That took me about three days! But I have singularly failed to get it to work with multiple attachments.

 I then tried to build an ordinary .desktop (actionned by clicking it) to add several attachments using hard-coded names. I thought if I could get that working I could then try to substitute them out from the %U variable presented by PCMANFM. Alas, I cannot get it to open thunderbird with multiple attachments.

I know this can be done because nemo can do it.... but, believe me, offering a new convert two file managers with different look/feel/capabilities is utterly bewildering! I want to stick with PCMANFM.

So here is my 'right-click' .desktop which will attach a single file to a new thunderbird composition 

```
[Desktop Entry]
Type=Action
Name=Send via Thunderbird
Tooltip=Send via Thunderbird
Profiles=profile-on_file;
Icon=thunderbird

[X-Action-Profile profile-on_file]
Name=Default Profile
MimeTypes = all/allfiles;
SelectionCount = %c
Exec = thunderbird -compose "attachment='%U'"
```

And here is my latest attempt at a standard .desktop to open multiple attachments

```
[Desktop Entry]
Name=thunderbird
Comment=thunderbird
Exec=thunderbird -compose "attachment='/home/myusername/Pictures/THE_ROCK/blue.jpg' '/home/myusername/Pictures/THE_ROCK/red.jpg'" 
StartupNotify=true
Terminal=true
Type=Application
Icon=system-file-manager
```
I think it's the way quotes, spaces and commas are used in .desktop files and/or thunderbird..... I have tried so many combinations I've lost count!

Any ideas anyone, please?

---

### Post by vasa1 on 2014-08-24
> **graylinux said:**
> ... I assured him if it could be done in XP it could be done in Lubuntu!.I have now spent days on it! 
...
Any ideas anyone, please?
Sorry, no ideas but please advise the user to read [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by graylinux on 2014-08-25
Hi 

I agree with the writer's points but nevertheless reliably adding right-click menus would benefit the converted as well as new convertees. 

I have discovered the mozilla site which indicates the correct notation should be:-

Exec=thunderbird -compose "attachment='/home/myusername/Pictures/THE_ROCK/blue.jpg,/home/myusername/Pictures/THE_ROCK/red.jpg'"

but this does not work. So maybe it's the way quotes are handled in .desktop files?

thanks

---

### Post by vasa1 on 2014-08-25
> **graylinux said:**
> Hi 

I agree with the writer's points but nevertheless reliably adding right-click menus would benefit the converted as well as new convertees. 

I have discovered the mozilla site which indicates the correct notation should be:-

Exec=thunderbird -compose "attachment='/home/myusername/Pictures/THE_ROCK/blue.jpg,/home/myusername/Pictures/THE_ROCK/red.jpg'"

but this does not work. So maybe it's the way quotes are handled in .desktop files?

thanks
My purpose in pointing to that link was to make users aware that there will be differences and that there will be "shortcomings" depending on one's point of view; otherwise, they'll be needlessly disillusioned.

Coming to the .desktop file, one way around the issue could be the use of **bash -c**. I'm not an expert in this and so I suggest you post exact examples, more than one will be better, of what you tried and any result including responses in the terminal. And you may improve your chances of getting a response by making the title a bit broader and indicative of the issue and posting in the "[Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")" section of the forums. I'd suggest something like "commas, spaces, quotes in .desktop files possible"? If you make the title too long, the forum may truncate it so make sure the good stuff is at or near the beginning!

My only experience with **bash -c** is here:```
Exec=bash -c 'GTK2_RC_FILES=/usr/share/themes/Greybird/gtk-2.0/gtkrc libreoffice --calc %u'
``` which is what I use to launch LibreOffice Calc with a non-default theme. That's a modified Exec= line from my **/usr/share/applications/libreoffice-calc.desktop**

All the best.

---

### Post by graylinux on 2014-08-26
Hi

Thanks for the tip with bash straight from the .desktop exec command... I may have a tinker.

In the meantime, I seem to have got this working by calling a bash script from the .desktop file. So:-

in my .desktop file in  /home/my_username/.local/share/file-manager/actions

```
[Desktop Entry]
Type=Action
Name=Send via Thunderbird
Tooltip=Send via Thunderbird
Profiles=profile-on_file;
Icon=thunderbird

[X-Action-Profile profile-on_file]
Name=Default Profile
MimeTypes = all/allfiles;
SelectionCount = %c
Exec=send_via_thunderbird.sh %U 
```

In the bash script, send_via_thunderbird.sh,  in /usr/local/bin I have:-
```

#!/bin/bash
# call thunderbird with -compose option and attach files as selected in pcmanfm
# called by .desktop in /home/my_username/.local/share/file-manager/actions

args=("$@")

new_string = ""

for i in "${args[@]}"
do
    new_string="${new_string},"
    new_string="${new_string}$i"
done

new_string="${new_string/,file:/file:}"

thunderbird -compose "attachment='$new_string'"
```

Seems to be working well....  

HTH someone... thanks

---

