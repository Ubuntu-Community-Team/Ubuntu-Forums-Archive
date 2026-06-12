---
title: "auto run of perl script"
date: 2009-06-01
forum: General Help
---

### Post by calvinlyp on 2009-06-01
hi all,

i am retively new to linux platform.
i have two pc each beinginstalled with ubuntu 8.10 and xubuntu 8.10.

i required to create a bash file in order to run a perl script automatically after it boot up.

may i know how about to create one?

below is some how i did a little research but not quite sure how to turn into a bash file and where to store it.


<code>
[SIZE=2][FONT=Calibri, Verdana, Helvetica, Arial][COLOR=#000080]#!/bin/bash
. /etc/Schedg/SCHEDG_CONFIGS

#<some commented stuff deleted here>

export PORT=`basename $PWD`
sleep 60
exec setuidgid $USER   $HOME/Schedg/bin/schedg_client.pl --configfile $CLIENT/$HUB-$PORT >> /tmp/$HUB-$PORT.out 2>&1[/COLOR][/FONT][/SIZE]
</code>

---

### Post by squaregoldfish on 2009-06-02
You have two options here.

You can add your code to /etc/rc.local, which is a script that's executed at boot time. However, note that this is a sh script, not a bash script, so the syntax of setting environment variables may be slightly different.

Alternatively, you can put your code into a file of its own, and then call it from rc.local. I suggest you put it in /usr/local/bin. Don't forget to make it executable! This would be my preferred option, as it keeps rc.local nice and clean, and also means you can run the script at any other time without problems.

Steve

PS To format code snippets nicely in these forums, select your code section and press the # button at the top of the editing box!

---

### Post by calvinlyp on 2009-06-09
> **squaregoldfish said:**
> You have two options here.

You can add your code to /etc/rc.local, which is a script that's executed at boot time. However, note that this is a sh script, not a bash script, so the syntax of setting environment variables may be slightly different.

Alternatively, you can put your code into a file of its own, and then call it from rc.local. I suggest you put it in /usr/local/bin. Don't forget to make it executable! This would be my preferred option, as it keeps rc.local nice and clean, and also means you can run the script at any other time without problems.

Steve


i am not able to find /etc/rc.d directory.
what i have is rc0.d to rc6.d plus there is another folder name rcS.d.

i look into each of those folders mention above, they do not contain another folder call rc.local.

may i know how do i make the script executable?
as i got two ways but both output the same thus do not know which is correct?
1)chmod a+rx myscript
2)chmod 755 /etc/myscript 

please advise

---

### Post by squaregoldfish on 2009-06-11
rc.local is a plain file in the /etc directory - it's not a directory itself.

As for making the script executable, both your options are equivalent, and do exactly the same thing. Have a read up on chmod (there's plenty of tutorials around) if you want to know how it works and what the different options are.

Steve.

---

