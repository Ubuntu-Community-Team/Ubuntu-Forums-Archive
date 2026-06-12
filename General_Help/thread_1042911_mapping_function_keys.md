---
title: "mapping function keys"
date: 2009-01-18
forum: General Help
---

### Post by rweaver4 on 2009-01-18
I am very new to Ubuntu and I use MFK (My Function Keys) in windows to map text to the 12 function keys on my logitech keyboard, for filling in forms etc.
Is there a similar product available that will perform this function in Linux?
I have tried running MFK under WINE but no go.

Any suggestions?
Thanks,
weaver00

---

### Post by jpkotta on 2009-01-18
There should be a keyboard shortcut entry in the settings menu.  I know it's there and it's easy to use, but I don't use Gnome so I can't look up exactly what it is.

Now, I don't think it has an easy way to type out text.  But it is possible to do this.  

Install xte:
```
sudo aptitude install xautomation
```

Then edit a file, we'll call it ~/bin/my_func_keys.sh.
```
#!/bin/bash

usage()
{
    echo "Usage: $0 FXX"
    echo "Prints a string to the window with focus."
    echo "There are 12 different possible strings."
    echo "Example: $0 F3"
    exit 1
}

if [ -z "$1" ] ; then
    usage
fi

str=""
case "$1" in
    F1)
    str="pressed F1"
    ;;
    
    F2)
    str="pressed F2"
    ;;

    F3)
    str="pressed F3"
    ;;

    F4)
    str="pressed F4"
    ;;

    F5)
    str="pressed F5"
    ;;

    F6)
    str="pressed F6"
    ;;

    F7)
    str="pressed F7"
    ;;

    F8)
    str="pressed F8"
    ;;

    F9)
    str="pressed F9"
    ;;

    F10)
    str="pressed F10"
    ;;

    F11)
    str="pressed F11"
    ;;

    F12)
    str="pressed F12"
    ;;

    *)
    usage
    ;;
esac

if [ -n "$str" ] ; then
    xte "str $str"
fi


```

Finally make it executable:
```
chmod +x ~/bin/my_func_keys.sh
```

Test it:
```
my_func_keys.sh F3
```

Now you can edit the script to output the strings you want, and bind keys to calling the script.

xte is a very neat program: you can send keypresses, mouse clicks, and move the pointer from scripts.

---

### Post by rweaver4 on 2009-01-24
Many thanks for your response, sorry I didn't respond earlier, As I said I am very new to Ubuntu/Linux and haven't the vaguest idea how to apply your solution! I will however read and learn, so if you can point me to any starters resources I woul be very grateful.

Thanks,
rweaver4

---

### Post by jpkotta on 2009-01-25
Did you find the keyboard shortcuts in the menu?

---

### Post by rweaver4 on 2009-01-27
Yes, I have checked the keyboard shortcuts, but what I was looking for was a facility to assign text to the function keys for filling in forms or entering user names etc.
For example MFK allows me to assign my street address to f1, my full name to f2, my telephone number to f3 etc. etc.
I am currently working my way through the UBUNTU book but as yet have no experience in writing macros or editing files.

Thanks for your responses
rweaver4

---

### Post by jpkotta on 2009-01-28
This is going to be slow if you don't tell me what you're stuck on.

Did you install xautomation?
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Did you edit a file like I posted?  You edit the quoted lines to set what it should paste
```
case "$1" in
    F1)
    str="123 Fake St. N"
    ;;
    
    F2)
    str="Jon Q. Publick"
    ;;

    F3)
    str="701-555-1234"
    ;;
```

---

### Post by rweaver4 on 2009-01-28
Again I thank you for taking the time to respond to my questions, my major problem is that I am a complete beginner and recently installed Ubuntu to learn about Linux, having no previous experience of linux. 
I will get there, but my object was to try to achieve an interface that I could use and then try to delve in to the intricacies of linux. 
Hence when you instruct me to 'edit a file', I search the net for instructions on how one edits a file under linux. I will install xautomation and work out how to apply your instructions. I am not actually 'stuck' on anything, I am just learning a new language and am many miles behind your knowledge and terminology.
Many thanks for your help,
rweaver4

---

### Post by jpkotta on 2009-01-28
> Hence when you instruct me to 'edit a file', I search the net for instructions on how one edits a file under linux.

Oh, I see that you said that earlier now.  Isn't it in the menu, in an obvious spot?  

You edit files just like in Windows.  You start an editor, and type text in it, and save when you're done.

Like I said before, I don't use Gnome, so I can't tell you _exactly_ how.  I think you can start gedit by pressing Alt-F2 to get the run dialog and type "gedit".

---

