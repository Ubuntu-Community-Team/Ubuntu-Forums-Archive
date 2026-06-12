---
title: "Help with tiny script"
date: 2006-01-27
forum: Desktop Environments
---

### Post by able on 2006-01-27
Somebody please help me with a tiny script as this:

Starts with a "yes" or "no" message box. If no then close, if yes then run a single command line.

---

### Post by ]Nbx*cmD[ on 2006-01-27
I think that's what you ask for:

```

#!/bin/bash
echo -e "yes/no? \n"
read s
if( test $s = yes ) then
    echo "You typed yes"
else
    echo "You typed no"
fi

```

---

### Post by kabus on 2006-01-27
In a terminal it would be easy :

```
echo "Do something (y/n) ? "
 read -n 1
        case $REPLY in
        y)
           do something
        ;;
        n)
           exit 0
        ;;
       *)
          echo "Usage:..."
          exit 1
        ;;  
        esac
```


If you want to display a graphical dialog box from a shell script you'll have to take a look at zenity (man zenity).

---

### Post by able on 2006-01-27
Thanks a lot for replaying.

I have now managed to walk the line as far as this:

```
zenity --question --title="Testing" --text="Do you want to proceed?"
   if [ "$?" = 0 ]; then
        zenity --title Replay --info --text 'You typed OK'
	else
        zenity --title Replay --info --text 'You typed Cancel'
   fi
```

Futher my goal is to replace the answer by typing "OK" and here directly execute a single comand line which I normally run from the terminal window. Is this possible?

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=able]Thanks a lot for replaying.

I have now managed to walk the line as far as this:

```
zenity --question --title="Testing" --text="Do you want to proceed?"
   if [ "$?" = 0 ]; then
        zenity --title Replay --info --text 'You typed OK'
	else
        zenity --title Replay --info --text 'You typed Cancel'
   fi
```

Futher my goal is to replace the answer by typing "OK" and here directly execute a single comand line which I normally run from the terminal window. Is this possible?[/QUOTE]

If you want to run a command instead of **zenity --title Replay --info --text 'You typed OK'**, just put that command in your script instead.

---

### Post by able on 2006-01-28
Very kind of you to help me step by step. Somebody help filling in the missing code line in bold?

```
zenity --question --title="Testing" --text="Do you want to proceed?"
   if [ "$?" = 0 ]; then
        **Here I want to open the terminal window with root privileges and in the root directory, i.e. cd /**
	else
        zenity --title Replay --info --text 'You typed Cancel'
   fi
```

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=able]Very kind of you to help me step by step. Somebody help filling in the missing code line in bold?

```
zenity --question --title="Testing" --text="Do you want to proceed?"
   if [ "$?" = 0 ]; then
        **Here I want to open the terminal window with root privileges and in the root directory, i.e. cd /**
	else
        zenity --title Replay --info --text 'You typed Cancel'
   fi
```[/QUOTE]
I think the line you want would be something like:
```

gksudo "nautilus /"

```

---

### Post by able on 2006-01-28
```
I think the line you want would be something like:

gksudo "nautilus /"

```

This opens Nautilus. Instead I want to open Terminal window with roots privileges and in root directory.

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=able]```
I think the line you want would be something like:

gksudo "nautilus /"

```

This opens Nautilus. Instead I want to open Terminal window with roots privileges and in root directory.[/QUOTE]
Sorry.  How about:
```

gksudo gnome-terminal --working-directory /  

```

---

### Post by able on 2006-01-28
A slight improvement did it:

```
zenity --question --title="Testing" --text="Do you want to proceed?"
   if [ "$?" = 0 ]; then
	foo=`gksudo -u root -k -m "Type password" /bin/echo "root access?"`
        sudo gnome-terminal --working-directory /
	else
        zenity --title Replay --info --text 'You typed Cancel'
   fi
```

I am very pleased getting helped.

---

