---
title: "Mapping keys to strings - is it possible - And HOW?"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by tipiglen on 2007-10-07
Hi all,

I'm a relative newbie, and have been trying to get something like the functionality of Autohotkeys (Windoze opensource).  

in particular, I would like to set a key (fn or otherwise) to return a string, say, to produce a bare html  link: <a href =""></a>, or a URL or email address to 'standard output', e.g. a form or comment window.

I've tried various methods involving modkeymap, special keymaps, the gconf-editor route, (which works in an extremely limited way to get some launches, but no strings)  

I've got no joy from all sorts of methods gleaned from searching the forums.  Many seem to work when input, but there is no result before or after rebooting.

One long thread seems to deprecate the idea of imitating the functionality of autohotkeys, because such functionality is already easy using scripts, etc., or some other basic gnu/linux method, but I can't find these methods.   I am probably overlooking something very obvious.

PLEASE HELP A POOR FOOL!

Thanks in advance
ed

---

### Post by jpkotta on 2007-10-07
It sounds like what you want is keybindings for a particular application (like an HTML editor), not global key bindings.  In that case, you need to figure out how to do this in your particular application, or find another app that has this feature if your current one doesn't.  To me, it doesn't seem useful at all to make F1 insert HTML tags when drawing in the GIMP, for example.  If you tell us which app you're concerned about, we may be able to help more.

---

### Post by tipiglen on 2007-10-07
"sounds like what you want is keybindings for a particular application (like an HTML editor), not global key bindings. "

Not really.  I want to be able to map keys to output my 'user-defined' strings, say into a wp document, or a browser form, etc.  They may be html fragments, as indicated, but I would also like to have default greetings, salutations, or common phrases, available in any text-based environment, perhaps including the terminals.  

I want something similar to a set of global 'aliases'.   I have made scripots which return phrases in the terminals in response, e.g the 'command' salaam, returns 

Salaam/Shalom/Shanthi/Dorood/Peace
Namaste  -ed

Not a lot of use in a terminal, but great in a Open Office document or browser form or email signature, etc.

There should be a simple way to map any user-defined string to an unused hotkey combination.

Where is it?

Salaam/Shalom/Shanthi/Dorood/Peace
Namaste  -ed

---

### Post by jpkotta on 2007-10-07
Maybe xclip can do what you want.

```
sudo aptitude install xclip
```
```
echo "this string is now in the clipboard" | xclip
```
Then you can middle click the string anywhere you want.  Clearly, you can make a script to do this and bind it to a key like a launcher.

---

### Post by tipiglen on 2007-10-07
jpkotta,

Thanks, but I don't think so.

I just want to get a keybinding to result in a text output  - simple (or should be)

I can't even get gconf-editor/metacity to set run_command_1 to a key which calls a script which does the job.  

global_keybindings:  run_command_1     <shift><alt> F8

keybinding_commands:   command_1    /home/ed/link

Press <shift><alt>F8:  Nothing!  Nothing! Nothing!

(link script):
#! /bin/bash
# link - script  to output a bare link
echo "<a href=\"\"></a>"
exit 0

script works fine in terminal:

ed@ubuntu:~$ link
<a href=""></a>
ed@ubuntu:~$ salaam
Salaam/Shalom/Shanthi/Dorood/Peace
Namaste  -ed
ed@ubuntu:~$ fullsalaam
Assalaam 'alaikum wa rahmatullaahi wa barakaatuhu
Peace, God's mercy and blessings be upon you
ed@ubuntu:~$ homepage
[http://home.btconnect.com/tipiglen/](http://home.btconnect.com/tipiglen/)
ed@ubuntu:~$ italquote
<i>""</i>
ed@ubuntu:~$ 

see?   Any ideas?  Any way to get gconf-editor to actually deliver?  or xbindkeys?  or ????

Thanks for the attempts

Assalaam 'alaikum wa rahmatullaahi wa barakaatuhu
Peace, God's mercy and blessings be upon you
ed

---

### Post by jpkotta on 2007-10-07
echo won't work.  It sends the string to stdout of the script, which is probably lost to the ether if you're calling the script from a keybinding.  There needs to be something that connects the keybinding with whatever window has focus.  This can be something in the window manager (since it can talk to all of the client windows) or something that talks to the X server.  I don't know for sure, but I doubt metacity has such an option (I could tell you how to do this in my WM of choice, FVWM, but you're not switchimg WMs for one feature).  Thus we need something that talks to the X server, like xclip.  I also saw something about xmbind and VirtualBindings, but it sounds pretty complicated.  

You could also try xse: [http://hpux.connect.org.uk/hppd/hpux/X11/Misc/xse-2.1/](http://hpux.connect.org.uk/hppd/hpux/X11/Misc/xse-2.1/)

Personally, I would be fine with xclip, because it achieves what you want: a simple way to insert a string with a keybinding, even though you need an extra mouse click.

---

### Post by tipiglen on 2007-10-08
jpkotta,

"echo won't work. It sends the string to stdout of the script, which is probably lost to the ether if you're calling the script from a keybinding."

It doesn't work inside the terminal, where both the focus and the script are, if 'called through a keybinding, but does as a command.  

I've tried xclip:
#! /bin/bash
# link script to output a bare link
echo "<a href=\"\"></a>" | xclip
exit 0

with limited success, but I don't have a mouse, and thus no middle button.  Just using the touchpad.  

It does work right here, for example, simultaneously clicking right and left buttons:
<a href=""></a>

It does work with clicking both buttons in a firefox reply/comment form, and in an open office document, and that's an improvement over all previous methods and it doesn't seem to do  a 'newline' (\n) .

There must (and should) be a simpler way.

Thanks for the help.
Salaam/Shalom/Shanthi/Dorood/Peace \n Namaste  

ed

---

### Post by njknight on 2007-10-08
Hi just to add my thoughts - I've also searched high and low for a program that will do for Linux what shortkeys does in Windows - but to no avail.  It is one of my most missed functions.  The ability to be able to define and type an 'abbreviation' and for the full associated text string to be inserted into an open word processor document / email / or editor makes life so much easier - but sadly in Linux, there's nothing that comes even close - and I've tried.............your only option (sadly) is to create a scap document (on the desktop) and create your 'phrases' within it.  Then copy and paste as normal.  The text clipboard utility Glipper does help in this, insomuch that it remembers the last elements copied to the clipboard - but this long winded way is just no comparison to the 'shortkeys' aplication available within Windows (which can be started with windows so that your pre- defined phrases are instantly and globally available, to ANY text based application.

If ever you come across an application under Linux  - do let me know

---

### Post by tipiglen on 2007-10-08
Thanks to njknight and jpkotta and some thinking/experimenting:

<alt>1, followed by ctrl-v gets me what I wanted.

First make a script:

#! /bin/bash
# mousequote script to output two verses of Burns
echo "I'm truly sorry man's dominion, 

 Has broken nature's social union, 

 An' justifies that ill opinion, 

 Which makes thee startle 

 At me, thy poor, earth-born companion, 

 An' fellow-mortal! 

  ............

 Still thou art blest, compar'd wi' me

 The present only toucheth thee:

 But, Och! I backward cast my e'e.

 On prospects drear!

 An' forward, tho' I canna see,

 I guess an' fear!



 Robert Burns, R.I.P. (To a Mouse)

                  http://www.robertburns.org/works/75.html" | xclip -sel clip
exit 0
#####

NOTE: using xclip option -sel(ect) clip(board) sends it to the ordinary clipboard, thus enabling pasting via ctrl-v   To install xclip, see jpkotta below.

This script is then saved to your home directory, subdirectory "bin".  
If you don't have a bin subdirectory, make one:

ed@ubuntu:~$ mkdir /home/ed/bin

save your scripts in it as created in text editor (gedit or other)
then make them executable by all:

ed@ubuntu:~$ chmod -R 700 /home/ed/bin
ed@ubuntu:~$ 

and make sure your subdirectory is on the PATH

ed@ubuntu:~$ sudo gedit /etc/environment
Password: (enter your user password, and gedit will launch)
This is the line to edit:
PATH="/home/ed/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
 (I added "/home/ed/bin:" at beginning, saved, and exited gedit)  the terminal prompt returns:
ed@ubuntu:~$ 

Then you must assign keybindings.  I used gconf-editor.  alt-F2 type gconf-editor and click 'run'.

Navigate to apps/metacity/keybinding_commands  and find command_1  command_2 etc.
The 'value' field of these commands will be empty.  enter the path to your script as value for command_1 (or whatever):
 /home/ed/bin/mousequote

Then navigate to global_keybindings (next one up in apps/metacity) and set run_command_1 to <alt>1 (or whatever key combination you want to use)  It will show "disabled", but if you click it you can enter your key-combo.
I've noted very few applications using the number keys with <alt>, so that's what I'm using.

exit gconf-editor (file/quit)

And try <alt>1 followed by <ctrl>v:

I'm truly sorry man's dominion, 

 Has broken nature's social union, 

 An' justifies that ill opinion, 

 Which makes thee startle 

 At me, thy poor, earth-born companion, 

 An' fellow-mortal! 

  ............

 Still thou art blest, compar'd wi' me

 The present only toucheth thee:

 But, Och! I backward cast my e'e.

 On prospects drear!

 An' forward, tho' I canna see,

 I guess an' fear!



 Robert Burns, R.I.P. (To a Mouse)

                  [http://www.robertburns.org/works/75.html](http://www.robertburns.org/works/75.html)

It works!  Whoopee!

Former heavyweight boxing champ Muhammad Ali

    visited the ruins of the World Trade Center on

    Thursday. When reporters asked how he felt about

    the suspects sharing his Islamic faith, Ali

    responded pleasantly, 'How do you feel about

    Hitler sharing yours?'

Assalaam 'alaikum wa rahmatullaahi wa barakaatuhu 
Peace, God's mercy and blessings be upon you

xx
ed

---

