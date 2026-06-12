---
title: "How to set no wrapping in Terminal?"
date: 2009-02-11
forum: General Help
---

### Post by abcuser on 2009-02-11
Hi,
using Ubuntu 8.10. When executing some command from terminal I get mess on screen because width of Terminal is too smaller.

How do I set no wrapping in Terminal?

Workaround is to set command to file and open it with Vim editor then executing command:
:set nowrap

To access text not seen by default, you can move with right key.

But this is not the best solution - sending commands to files is time consuming. Is there any way I can set Terminal width without sending output to file?

P.S. In Windows this is set by using Properties | Layout | Width by using cmd program.

How to do the same in Linux?
Regards

---

### Post by sdennie on 2009-02-11
This seems really dangerous to me (you potentially miss important information).  I'd be surprised if you can do this with gnome-terminal.

---

### Post by abcuser on 2009-02-11
Hi,
in Windows there is slider at bottom any you can scrool to right. In Vi editor you can always move to right with right key to see the remaining of the text. So I don't see any problem of not seeing the text.

I hope there is something in Terminal because this is making me crasy for years...
Regards

---

### Post by abcuser on 2009-02-12
Hi,
according to man pages stty command is used to set width of terminal.

I tried the following:
```
stty -a
```
to get info about column width and by default is set to 157

Then I executed:
```

stty columns 500

```

Checked the settings stty -a and columns value is set to 500.

If a write very large string to file using "echo xxxx > file" and then use cat command to read it the output is still the same.

Any idea?
Regards

---

### Post by abcuser on 2009-02-15
Hi,
I have found two work around solutions:
1. use less command to overcome this problem:
```
some_command | less -S
```
2. instead of using gnome-terminal use terminal program that is capable of using no wrapping like Terminator
[http://software.jessies.org/terminator/#downloads](http://software.jessies.org/terminator/#downloads)
Terminator has a horizontal scroll bar so no wrapping at all.

Note: this Terminator program is not the same program that is already included in repository (two programs with the same name!), so do NOT use: "sudo apt-get install terminator". Instead install deb package from above web site.

If someone out there is having some other solution I would be very happy to test it out.
Regards

---

### Post by j_kubik on 2010-11-18
I found this script on the net:
```
function nowrap { cut -c -`tput cols`; }
```
which is executed like
```
echo "something very long" | nowrap 
```
Also possible
```
echo "something very long" | cut -c -`tput cols`
```

However if you have any escape characters in printed data, they will get removed. Also it might have problems with multi-byte characters (eg. asian languages?).

Also script needs adding some tests before printing in case it's started without terminal. If you want to include this function in some bigger script, that would be advisable.

---

