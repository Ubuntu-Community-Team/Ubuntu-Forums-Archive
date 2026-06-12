---
title: "Auto XP partion restore"
date: 2009-01-22
forum: General Help
---

### Post by Zewbie on 2009-01-22
At my computer shop where I work, we got alot of used PC's from some place.  It's my job to refurbish them for resale.  Each computer comes with XP pro.  So the boss man asks me if there is a way to put a XP restore option.  I say yes if I install Linux on a small partion and use partimage to make a image of the XP partion and store in on the Ubuntu side. I wrote a small shell script so the end user could restore XP without having to bring it in theshop when they foul XP up.

Here is the script:

```

#!/bin/bash
# System Restore


echo "***************************** XP System Restore *****************************" 
read -n 1 -p "Press any key to continue"

echo "This will restore your Windows XP installation"
	
echo "********************YOU WILL LOSE ALL DATA IF YOU CONTINUE********************"
echo "ONLY RUN THIS IF YOU WANT A FRESH INSTALL OF XP"
echo "Y to continue N to exit Y/N"

read a
	if [[ $a == "N" || $a == "n" ]]; then
		read -n 1 -p "Press any key to continue..."
		exit

		else

	if [[ $a == "Y" || $a == "y" ]]; then
	 	echo "Restore System Now? **Warning** ALL DATA WILL BE ERASED!! Y/N?"
		read a
	if [[ $a == "N" || $a == "n" ]]; then
		exit
		else
	if [[ $a == "Y" || $a == "y" ]]; then
		read -n 1 -p "Press any key to continue... The password is owner"
		sudo partimage restore /dev/sda1 /home/owner/XP-Restore.000
        
  	fi
	fi
    fi
fi

```

It works fine but not simple enough for end users (So the Boss Man says).  So I edited GRUB so it would only give two options "Windows XP Pro" and "System Restore"--Ubuntu--.

Is there a way to have the script auto run on boot or login and have partimage restore without any input from the end user other then the Y/N questions that I have in the script.

If anyone can help me out here it would be greatly appreciated :)

---

### Post by Zewbie on 2009-01-23
"Bump"

Can someone help

---

### Post by Zewbie on 2009-01-23
Would the use of flag -BX work here.

* -BX, --fully-batch=X batch mode without GUI, X is a challenge response string


I don't understand the batch = X part...  is the X meant to be replaced with something or would the command just look like this?

```

sudo partimage restore -BX /dev/sda1 /home/owner/XP-Restore.000

```

---

### Post by Zewbie on 2009-01-24
Anyone...Anything?

#Apple II/a code

10 PRINT "BUMP"
20 GOTO 10


BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMP
BUMPBUMP
BUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMP
BUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMPBUMP

---

### Post by Zewbie on 2009-01-25
Does anyone know of another place I could post this thread where I could get some feed back on this topic?

---

### Post by Zewbie on 2009-01-27
can anyone even see this threat?

---

### Post by r0g on 2009-03-12
This blog has some into on the -BX option although I'm still not entirely clear on it (hence ending up here!)...

[http://timwise.blogspot.com/2007/04/running-partimage-in-batch-mode.html](http://timwise.blogspot.com/2007/04/running-partimage-in-batch-mode.html)

---

### Post by MaxIBoy on 2009-03-12
To make it run automatically, add it to the initscripts:
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Might I suggest using something besides Ubuntu? Because Ubuntu is overkill for what you need. A Debian minimal install will do the trick just fine. To get the minimal install, use the "net install" CD and don't download any packages from the Internet. This will leave you with a minimal working system.

---

