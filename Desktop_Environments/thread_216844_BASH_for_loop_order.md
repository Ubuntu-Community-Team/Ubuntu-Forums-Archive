---
title: "BASH for loop order"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mikeym on 2006-07-16
Hi,

I'm having a spot of difficulty with my first proper-ish BASH script. I'm trying to read files from a directory - in this case .nzb files - and execute a program once for each file, passing the file's name as a parameter to the program. 

At the moment however it is somehow bundling up all the call parameters and calling the program once for the whole lot.

This is a problem becasue the progam wont run at all if it encounters a problem in one of the files. I also want to be able to capture the exit status of each run of the program. This is also causing a problem as the progam seems to give an exit status of "0" even when a problem has been encountered. On top of this problem is the fact that the program tries to create a text graphics environment which makes it difficult to capture the output from it as it quickly becomes too large.

Hopefully you can help with some of these problems. :)

Here is my script:

```

function PrintUseage {
        echo Useage: $0 [options]
        echo Options:
        echo -cron      Restrict graphical output for cron.
        echo -shutdown  Shutdown the computer on completion.
}

function Callnzbperl {
        # Run 'nzbperl'.
        # If 'cron' redirect output to /dev/null as graphics
        # create too large a file to log. Errors are also noisy.
        if [ "$USECRON" = "1" ]; then
                # Running from cron - hide graphics.
                date +"%F %T Running 'nzbperl.pl'." >> /var/log/getnzbfiles.log
                nzbperl.pl "$1" >> /dev/null 2>> /dev/null
                echo "$?"
        else
                # Running from command prompt.
                date +"%F %T Running 'nzbperl.pl'." >> /var/log/getnzbfiles.log
                nzbperl.pl "$1" 2>> /dev/null
                echo "$?"
        fi
}

# Make sure that the download directory exists.
mkdir $HOME/nget 2> /dev/null

# Export preferences as these aren't set by 'crontab'
# make sure to pretend to be 'xterm' because 'nzbperl' crashes
# without a valid term setting.
date +"%F %T Exporting preferences." >> /var/log/getnzbfiles.log
export PATH=$PATH:$HOME/bin:/usr/local/bin:/usr/bin
export TERM=xterm

# Read options from shell arguments.
USECRON=""
USESHUTDOWN=""
while (( "$#" )); do
        if [[ "$1" = "-cron" ]]; then
                USECRON="1"
        elif [[ "$1" = "-shutdown" ]]; then
                USESHUTDOWN="1"
        else
                PrintUseage
                exit 1
        fi
        shift
done

# Run 'nzbperl' for each 'nzb' file seperately so we can read the
# error codes indevidualy.
for NZBFILE in "$(find /mp3/dvd/nzb -iname *.nzb -maxdepth 1 2> /dev/null)"; do
        echo "$NZBFILE"
        Callnzbperl "$NZBFILE"
done

# Fix ownership permissions on the /mp3/dvd folder
date +"%F %T Fixing ownership permissions '/mp3/dvd/'." >> /var/log/getnzbfiles.log
fixdvdownership

if [ "$USESHUTDOWN" = "1" ]; then
        # Shutdown the computer now we're done!
        date +"%F %T Sending system shutdown command." >> /var/log/getnzbfiles.log
        myshutdown
fi
exit

```

Here is my current output from the script when an error is encountered:

```

/mp3/dvd/nzb/TestR.nzb
/mp3/dvd/nzb/TestF.nzb
/mp3/dvd/nzb/TestO.nzb
Reading config options from /home/mikey/.nzbperlrc...
uudeview found: /usr/local/bin/uudeview

  nzbperl version 0.6.8, Copyright (C) 2004 Jason Plumb
  nzbperl comes with ABSOLUTELY NO WARRANTY; This is free software, and
  you are welcome to redistribute it under certain conditions;  Please
  see the source for additional details.

Checking for availability of newer version...
Look like you're running the most current version.  Good.
Loading and parsing nzb file: /mp3/dvd/nzb/TestR.nzb
/mp3/dvd/nzb/TestF.nzb
/mp3/dvd/nzb/TestO.nzb

 Sorry, but nzb file is broken!  The xml could not be parsed:

 Couldn't open /mp3/dvd/nzb/TestR.nzb
/mp3/dvd/nzb/TestF.nzb
/mp3/dvd/nzb/TestO.nzb:
No such file or directory at /usr/local/bin/nzbperl.pl line 2126

 *** nzbperl requires valid, well-formed XML documents.

0

```

As you can see the 3 files each being called with nzbperl.pl is resulting in only one call to nzbperl.pl.

Is the script trying to be clever and just open one instance?

---

### Post by philippe_carlo on 2006-07-16
You need to set the internal field separator (shell variable IFS) to linefeed as follows:

IFS="
"

(the newline is very important)

---

### Post by mikeym on 2006-07-16
I have tried this in all the places i could think of and it doesn't seem to work. 

I'm not quite sure what you are getting at, from what I can tell the IFS tells shell which characters to split commands and argument inputs using, but I'm trying to call the program 3 separate times using separate strings. 

Unless you are suggesting that it is storing up parameters into a big string with each parameter on a new line and then calling the function once?

---

### Post by philippe_carlo on 2006-07-16
That's the idea. That's how I do it, usually.

---

### Post by mikeym on 2006-07-16
I have tried replacing the for loop that calls the program with this to see if it would help:

```

# Run 'nzbperl' for each 'nzb' file seperately so we can read the
# error codes indevidualy.
LIST="$(find /mp3/dvd/nzb -iname *.nzb -maxdepth 1 2> /dev/null)"
IFS="
"
Callnzbperl "$LIST"

```

But still no change in it's function. I'm not sure that this is the right approach.

---

### Post by mikeym on 2006-07-17
Thank you for your post you were one step ahead of me. 

It wasn't helping with the first problem, but as soon as I had fixed that I could see what you were trying to say.

The problem I was having was that I had placed my 'find' command in my for loop inside quotes so that it was only going round the for loop once.

Once I had removed these it worked well until I tried a file with a space in it and because the IFS defaults to [Spaces], [Tabs] and [New Lines], and find prints out its file-names with spaces and no backslashes, IFS has to be set to only split in the caes of [New Lines].

---

