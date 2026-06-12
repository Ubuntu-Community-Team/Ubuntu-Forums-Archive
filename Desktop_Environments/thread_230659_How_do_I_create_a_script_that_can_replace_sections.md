---
title: "How do I create a script that can replace sections of text"
date: 2006-08-06
forum: Desktop Environments
---

### Post by TuxCrafter on 2006-08-06
How do I create a script that can replace sections of text.

Hello I would like to have a script that searches a file for a given text block like a device section of xorg.conf. and replace it with  another one. that way I can write scripts that change the xorg file automatic by replacing sections.

I know of the tools sed cat tail head cut etc. But it would be nice if someone has a script. These tools.

If I take the problem apart for analysing. It should do something like this.

I look for a text string in a file. I want the line number were it starts. (example: Section "Device"
Then I look for a text string that indicates the end of the block that I search (example: EndSection)

Now I have to line numbers the beginning and the end and remove this block. 
Then I add my one text at the first line number. 

I also would like to do this with config params something like this:
there is a file with a param AsUser = "true"

Now I want to automatic chach the param to false.

Or I want to search for a string "begin" and "end" and if between those string is a string "user" then I want tho change is to something.

Does anyone have a example on how this is done?

---

### Post by Tomosaur on 2006-08-06
In my script, I use the VI/EX 'search and replace' command. The format is as follows:

:[RANGE]s/text to overwrite/replacement text/[flags]

The range and flags are optional. With no range, the command will only work on the current line. With a range of '%', the command will work on the whole file.

To be more specific, here's basically what I do to find a string in a file, and replace it. I will use your own example.

```

STRING_LINE_NUMBER=$(grep -n ^AsUser xorg.conf | grep -o ^[[:digit:]]*)
vi -e -c :"$STRING_LINE_NUMBER"s/true/false xorg.conf -c :wq

```

This finds the line number of the line which begins with 'AsUser', then hands control over to Vi, which jumps to that line, and replaces 'true' for 'false'.

This is only a very basic piece of code, but it works. Take a look at the script in my sig for more complex methods of doing what you need.

---

### Post by lamego on 2006-08-06
I have been doing a similar script today, please note that I didn't test it properly so use the code at your own risk :P

```
#!/bin/sh
# This script should take care of installing the ATI Driver and setting it up

function check_root()
{
  w=`whoami`
  if [ ! "$w" == "root" ]
  then
    echo "This script needs to be run with sudo !"
    exit 3
  fi
}

function check_required_package()
{
  echo -n "$1 -- "
  found=`dpkg-query -l $1 | grep -c "^ii"`
  if [ $found -eq 0 ];
  then
    echo "not found - install"
    zenity --question --text="Package $1 needs to be download and installed"
    if [ $? -eq 0 ];
    then
    	sudo apt-get install --assume-yes $1 
    	 if [ ! $? -eq 0 ];
    	 then
    	    zenity --warning --text="There was an error installing package $1"
    	    exit 2
    	 fi
    else
    	echo "Termination requested by user"
    	exit 3
    fi
  else
    echo "ok"
  fi
}

function x_org_change()
{
  section=$1
  item=$2
  value=$3
  found_section=0
  numlines=$(($(grep -c $ /etc/X11/xorg.conf)+1))
  n=1
  echo > /etc/X11/xorg.conf.new
  #cat /etc/X11/xorg.conf | {
  while [ $n -lt $numlines ]
  do
    line=$(head -$n /etc/X11/xorg.conf| tail -1)
    c_item=`echo $line | awk ' { print $1 }'`
    c_value=`echo $line | awk ' { print $2 }'`
    #echo $c_item $c_value
    if [ "$c_item" == "EndSection" ]
    then
      found_section=0
    fi
    if [ "$c_item" == "Section" -a "$c_value" == "$section" ]
    then
      found_section=1
    fi
    if [ $found_section -eq 1 -a "$c_item" == "$item" ]
    then
      line="	$item		$value"
      echo "$line" >> /etc/X11/xorg.conf.new
    else
      head -$n /etc/X11/xorg.conf| tail -1 >> /etc/X11/xorg.conf.new
    fi
    n=$(($n+1))
  done
}

# Check for required packages
check_root
echo "Checking for required packages..."
check_required_package xorg-driver-fglrx
check_required_package linux-restricted-modules-`uname -r`
check_required_package fglrx-control
echo "Backing up configuration to /etc/X11/xorg.conf.old"
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
echo "Creating /etc/X11/xorg.conf.new using the new driver"
x_org_change \"Device\" Driver \"fglrx\"
echo "Installing new configuration /etc/X11/xorg.conf.new -> /etc/X11/xorg.conf"



```

---

### Post by ardchoille on 2006-08-06
I know you can use this in a bash script to replace text in a file:

```

sed -i 's/old text here/new text here/g' /path/filename

```

The -i option edits the file in place and makes a backup if the extension is supplied. Read man sed for more info.

---

### Post by TuxCrafter on 2006-08-06
Thank you for the nice answers really great work.

I didn't now i could do such things with the vi editor 8)

---

### Post by TuxCrafter on 2006-08-06
Now we are at it :D 

How do a catch a warning/error form a program.

I want to use the mkdir command without sudo so that normal users can use it. but if they try to make a dir where the don't have permission mkdir says Permission Denied.

Now I would like to catch this error so that it will try again with sudo mkdir and the user must now enter a password.

How do I do this.

```
echo "creating directory "$extractpath""
error=`mkdir -v -p $extractpath`
echo $error
```

This did not work!

---

### Post by Tomosaur on 2006-08-06
Probably a better idea to run your script using sudo to start it if you know this kind of thing will happen. I personally wouldn't trust a script which asked me to input my password during runtime.

---

### Post by TuxCrafter on 2006-08-06
The script is part of a thunar script and it is annoying to ask for password if they are not necessary it also changes permissions. I only want to ask the password if they don't have enough permissions.

Better way is to add the program to the sudores list. I think i will do that but it would be nice to know how it is done in a script fur other purpose
how do you catch the exit code of a program?

PS you can trust gksu in a script right?

---

### Post by Tomosaur on 2006-08-06
Technically you can trust anything you put in it. The only reason I wouldn't trust a script asking me for my password is if I hadn't written it and hadn't gone through the code checking what it does. It's the same principle as giving a website your credit card details - you don't do it unless you're confident it's been checked and approved by you or someone you trust.

If the user has run a script directly from the terminal, they will see the output of the program unless you've redirected it using a pipe or something. You don't have to worry about catching and echoing it.

EDIT: But to actually catch the output of a program, just make a variable and set it to the output of the program in question, for example:
```

error=$(ls HAHAHAHAHAHHAHAA)
echo $error

```

will produce the output:

"ls: HAHAHAHAHHAHAHAHA: No such file or directory".

Different programs have different output though. Wget will show itself trying to resolve a server before it reports that it can't find one, for example. You may need to redirect the output to grep so you can isolate the error.

---

