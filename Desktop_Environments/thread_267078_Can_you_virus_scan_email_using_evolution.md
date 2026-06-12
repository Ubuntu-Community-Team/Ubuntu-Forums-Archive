---
title: "Can you virus scan email using evolution?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by IanM39 on 2006-09-28
Hi,

Can anybody clue me in on which filters I need to set up to scan my incoming and outgoing email using clamav and evolution.

I know there's an easy way to set this up with Kontact, but I prefer Evolution's interface.

Thanks for the help.

Ian

---

### Post by dcstar on 2006-09-29
> **IanM39 said:**
> Hi,

Can anybody clue me in on which filters I need to set up to scan my incoming and outgoing email using clamav and evolution.

I know there's an easy way to set this up with Kontact, but I prefer Evolution's interface.

Thanks for the help.

Ian

[http://www.ubuntuforums.org/showthread.php?t=84423](http://www.ubuntuforums.org/showthread.php?t=84423)

---

### Post by dpm on 2006-10-03
> **dcstar said:**
> [http://www.ubuntuforums.org/showthread.php?t=84423](http://www.ubuntuforums.org/showthread.php?t=84423)

I think hat thread is a bit misleading and difficult for new users. The main topic is a link to a website which discusses how to scan incoming e-mail with clamav if you are using **procmail, **but there is no mention to Evolution. The instructions require creating a PERL script to be invoked by procmail. If you are using Evolution you have to create a rule which invokes the script, which is explained on the ubuntuforums thread.

IMHO it is a lot easier to skip using the script altogether and call clamav from Evolution directly, as per the instructions from an evolution developer on this page:

[http://lurker.clamav.net/message/20050618.021537.f1ab6d55.en.html](http://lurker.clamav.net/message/20050618.021537.f1ab6d55.en.html)

It basically boils down to creating a new filter rule to scan all incoming e-mail with clamav:

Edit>Message Filtes>Add (make sure the drop-down list is set to "Incoming")

with the following program pipe:

```
 /usr/bin/clamscan --quiet -
```In any case, both methods are valid options.

Cheers.

---

### Post by BLTicklemonster on 2006-10-03
Viruses? In linux?

---

### Post by BLTicklemonster on 2006-10-04
[http://www.shellcode.com.ar/docz/binfmt-en.pdf](http://www.shellcode.com.ar/docz/binfmt-en.pdf) in english

[http://www.shellcode.com.ar/docz/binfmt-es.pdf](http://www.shellcode.com.ar/docz/binfmt-es.pdf) in espanol

Seems like there's something amiss after all. Won't be long before that's capped off, though.

I wonder if it's like that Firefox hoax we just went through, though...

---

### Post by dpm on 2006-10-04
> **BLTicklemonster said:**
> Viruses? In linux?

Let's just please not hijack the thread's topic and start yet another "linux is immune to viruses" thread.

Please.

---

### Post by dcstar on 2006-10-05
> **desp said:**
> I think that thread is a bit misleading and difficult for new users.
......

Yes, it is now because the relevant part that was once there is now gone!

Here is the script I use that pops up a message when CLAMAV detect a virus in my incoming Evolution e-mail:
```
#!/bin/bash
# Fred Blaise <chapeaurouge AT madpenguin DOT org>
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA

FILE=/tmp/$$_outclam.tmp
clamdscan - 1>$FILE

if [ $? -eq 1 ]; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
zenity --warning --title="Evolution: Virus detected" --text="$STRING" &

exit 1
fi

exit 0

```

This is in my system as /usr/local/bin/clam-filter with 777 permissions, and is called by the following Evolution Message Filter:

---

### Post by shane2peru on 2006-11-08
Ok, I have this setup, however I use Thunderbird.  Is there any way to do this in Thunderbird?  Thanks.

Shane

---

### Post by Spin Doctor on 2006-11-28
> **desp said:**
> ....IMHO it is a lot easier to skip using the script altogether and call clamav from Evolution directly, as per the instructions from an evolution developer on this page:

[http://lurker.clamav.net/message/20050618.021537.f1ab6d55.en.html](http://lurker.clamav.net/message/20050618.021537.f1ab6d55.en.html)

It basically boils down to creating a new filter rule to scan all incoming e-mail with clamav:

Edit>Message Filtes>Add (make sure the drop-down list is set to "Incoming")

with the following program pipe:

```
 /usr/bin/clamscan --quiet -
```

Allright. This does not work on Evolution 2.8.1 that comes with Edgy, since you cant send any parameters with the program pipe command. 
What I understand, you must be able to do that for this solution to work, as mentioned on the website above.

>  The dash is necessary to use it on data streams, the --quite option prevents scanning reports on STDOUT. See 'man clamscan' for more details.So does anyone out there virusfilter their Evolution 2.8.1 with Clamscan? And does have a nice solution to this.

Thanks!!

---

### Post by dpm on 2006-11-30
> **Spin Doctor said:**
> Allright. This does not work on Evolution 2.8.1 that comes with Edgy, since you cant send any parameters with the program pipe command.

Why does the pipe command ignore the arguments in Evo 2.8.1? Is there a bug report about that?

---

### Post by Spin Doctor on 2006-11-30
I attached a screenshot for you to see how it looks like. It is in swedish locale, but you should get the picture anyways =)

After the pipe to command selection, there is only a "browse" button. You cant enter any text or parameters in that field, you can only click on it, and then it opens up to a window where u can select a program. The problem is that you cant include any commandline parameters, which I understand is a must to activate virusscanning on incomming emails.

I guess launchpad is the way to go to see if a bugreport has been filed?

---

### Post by dcstar on 2006-12-02
> **Spin Doctor said:**
> I attached a screenshot for you to see how it looks like. It is in swedish locale, but you should get the picture anyways =)

After the pipe to command selection, there is only a "browse" button. You cant enter any text or parameters in that field, you can only click on it, and then it opens up to a window where u can select a program. The problem is that you cant include any commandline parameters, which I understand is a must to activate virusscanning on incomming emails.

I guess launchpad is the way to go to see if a bugreport has been filed?

There is no need, you just use the selected program and Evolution itself pipes the email to the program and then waits for the return code.

If you want any extra parameters, **you** put them in the program that **you** are calling (write you own script).

---

### Post by Spin Doctor on 2006-12-02
Well, I tried the option of just sending it directly to clamscan, but that solution does not work because:

> ...The dash is necessary to use it on data streams ...So it seems writing a script is the only way to solve this issue for me. I have never written a script before, so maybe you could link me to some place where I can read up on it, or just show me a quick example. That I would appreciate! Thanxs mate!

---

### Post by dpm on 2006-12-03
Ok, we'll create a simple script to be interpreted by the shell.

1. Open gedit

2. Paste the following lines onto the "Unsaved Document"

```
#!/usr/bin/env sh

/usr/bin/clamscan --quiet -
``` and exit gedit. 

3. Give a name to the document and save it somewhere (I saved it onto~/bin). I named my script clamevo.sh, you can call yours whatever you like. Note: the .sh extension is not required, you could have no extension and it will still be executed as a bash script (that's what the initial line of the script is for).

4. Change the file permissions to mark it as executable. Open a terminal, navigate to the folder where you saved your script and execute (remember, substitute clamevo.sh by whatever you named your script):

```
chmod +x clamevo.sh
```That's it. Now you can point the "Pipe to command" filter option in Evo to this script. A couple of notes:

the first line of the script (along with the file permissions) tells Linux that this is an executable script to be interpreted by the sh shell. The third line is the command to be executed by the shell.

I hope this helps.

---

### Post by Spin Doctor on 2006-12-03
Man, this is a tough one to get to work. 

I did exactly what u said. But the script is returning odd values. I did a test, and the return values that comes back to Evolution is somewhere between 100-1000. 

I looked in the man of clamscan, and the highest returncode is like 71. 

First I tried, if the return equals 1 send to my virusfolder. I attached my testvirus signature as an attachment, and it did not catch that one. So started to look for if it was working at all... 
Therefore I set the condition to if returncode is not 0 (not infected), move to virusfolder...and after that all emails moved into my virusfolder..even the good ones..that made me realize it is probably returning some error codes, but totally out of range..so something iffy about this one...

Any clue?

---

### Post by dpm on 2006-12-04
Now, I do not know about the return codes, but here's a couple of comments:

1.- The behaviour you have described as in the fact that the "Pipe to Command" option cannot take command-line arguments from the UI anymore is a known Evolution 2.8 bug: [http://bugzilla.gnome.org/show_bug.cgi?id=354797](http://bugzilla.gnome.org/show_bug.cgi?id=354797)

2.- It seems that the Evolution code still processes commands with arguments in the backend, only that you cannot set them in the UI anymore. So, you might want to try a new approach and enter the command directly in your **~/.evolution/mail/filters.xml** file (which is what the UI used to do before Evolution 2.8). In my case, I looked for the following lines:
```

        <part name="pipe">
          <value name="command" type="command">
            <command>**/home/dpm/bin/clamevo**</command>
```which I substituted as follows:

```
        <part name="pipe">
          <value name="command" type="command">
            <command>[COLOR=Red]**/usr/bin/clamscan --quiet -**[/COLOR]</command>
```Once you've saved your changes, you can then try to send an e-mail with a virus signature to yourself again and see if it works.

Cheers.

---

### Post by Spin Doctor on 2006-12-05
It is working!! By making the changes to the filter direct in the XML filter file, clamScan does work.  Finally! I see there is a bugreport on this whole issue aswell. 

I really appreciate your helping me solving this. 

//Spin Doctor

---

### Post by dpm on 2006-12-06
> **Spin Doctor said:**
> It is working!! By making the changes to the filter direct in the XML filter file, clamScan does work.  Finally! I see there is a bugreport on this whole issue aswell. 

I really appreciate your helping me solving this. 

//Spin Doctor

Glad I could help.

Cheers.

---

