---
title: "finding a file and opening it at the same time - in linux"
date: 2014-11-30
forum: Desktop Environments
---

### Post by dilbert_one on 2014-11-30
howdy dear ubuntuexperts 

hope you are all right and everything goes well.

This is probably an easy one, but I can't figure it out and it's pretty much not searchable.

on a linux-machine i have installed filezilla

the filezilla runs pretty well and all is ok.

now i need to have the passwd that i have stored years ago. The passprhase is stored in a plain in a file called sitemanager.xmlfile


I want to find that file and open it with a terminal command.

```
find . -name *.sitemanager

```

well i thought that this will return the file I'm looking for. Now how do I open it automatically, without typing the name?

```

find . -name *sitemanager.xm | open

```

This doesn't work. It says it doesn't found the open command.


question: why it does not work on opensuse?

should i use any other command - eg the following:

```

find . -name *xyz | xargs open

```
or

```
find . -name *sitemanager.xml | xargs open

```
or
```

find . -name *.xyz -exec open {} \;

```

and

```
find . -name *.xyz -exec open {} \; .

```

any and all help will be greatly appreciate

again: what is wanted and needet is to find out the passphrase in the filezilla-configuration

---

### Post by Lars Noodén on 2014-11-30
Try using  the 'gnome-open' after 'xargs'.

---

### Post by dilbert_one on 2014-11-30
hello dear lars nooden 



> **Lars Noodén said:**
> Try using  the 'gnome-open' after 'xargs'.


like so

```

find . -name *sitemanager.xml | xargs open gnome-open


``` 

note - i run kde not gnome 
should i use some simmilar for kde?

---

### Post by Lars Noodén on 2014-11-30
Maybe "xdg-open" is there, I probably should have mentioned that one instead.  I don't have Kubuntu available at the moment, though I used to have it a long while back.

---

### Post by dilbert_one on 2014-11-30
hello again many many thanks for the reply

well  i should have mentioned this. i run opensuse linux 13.1 with kde


again - many many thanks for the quick reply

i tried some things:

```

find . -name "*sitemanager.xml" | xargs less

```

runs nice - but does not open the file


```

find ./ -name "*sitemanager.xml" -exec cat {} \;
```

runs but has got no permissions to do any thing with the results


see below

```

find ./ -name "*sitemanager.xml" -exec cat {} \;
linux-70ce:/ # ls | grep filezilla.xml | xargs open
xargs: open: Datei oder Verzeichnis nicht gefunden
linux-70ce:/ # ls | grep recentservers.xml | xargs open
xargs: open: Datei oder Verzeichnis nicht gefunden
linux-70ce:/ # find ./ -name "*sitemanager.xml" -exec cat {} \;
find: ‘./var/run/user/1000/gvfs’: Keine Berechtigung
find: ‘./run/user/1000/gvfs’: Keine Berechtigung
linux-70ce:/ # 


```


note keine berechtigung means - no permission 
this is very very funny - since i run this command as a superuser ! Isnt this very funny?



well months ago i had a code that was runnng and opening the fine .  - with another file that i needed to edit. the file was opendd in kwrite or kate

but now i have no luck 

see another idea like so

```


find . -name *sitemanager.xml | xargs open gnome-open


```

but wait - this does not run as well  - since i run kde and not (!!!!) gnome 


do you have any other ideas to get a solution?


any and all help will be greatly appreciated

---

### Post by Lars Noodén on 2014-11-30
```

 find . -name 'sitemanager.xml' -exec xdg-open "{}" \;

``` 

I just noticed that you had an extra asterisk.  If the filename was not enclosed in quotes then it might have expanded in the shell.  If xdg-open is not available on your system then kde-open might be there.

---

### Post by dilbert_one on 2014-11-30
i tried this command - but i guess that i have permissions-problems


many many thanks for the hints - well i looged as root 
 
```
 linux-70ce:/home # cd..
linux-70ce:/ # grep Pass ~/.filezilla/sitemanager.xml
grep: /root/.filezilla/sitemanager.xml: Datei oder Verzeichnis nicht gefunden
linux-70ce:/ # grep Pass ~/.filezilla/sitemanager.xml
grep: /root/.filezilla/sitemanager.xml: Datei oder Verzeichnis nicht gefunden
linux-70ce:/ # grep Pass ~/.filezilla/filezilla.xml
grep: /root/.filezilla/filezilla.xml: Datei oder Verzeichnis nicht gefunden
linux-70ce:/ # 


```

all the results were telling that i have the directory or the file cannot be found... 

well this is so funny - 

a. i have installed filezillla on the machine 
b. the passwd ( or passphrase)  is written in a xml-file
c- it is written in plaintext

by the way - there are more things to do: 

eg - the the next step i to tomorrow.

```

Use "ls -l /pathtofile/file to print its permissions and find out why.
```

well i guess that this is a key step


i do more tests on this tomorow

untill then

btw - i also tried out the followning 

we ve have to choose which editor we want to open the file in and use the proper command for that editor. For example:
```

find ./ -name 'blah' -exec vim {} \;
```

but - hmm i guess that i had no luck with this

---

### Post by papibe on 2014-11-30
Hi dilbert_one.

Most of the above suggestion to find and open a file work.

Test this:
```
$ echo "This is a test file." > ./test_file.txt

$ ls test_file.txt
test_file.txt

$ cat test_file.txt
This is a test file.

$ find -name 'test_file.txt'
./test_file.txt

$ find -name 'test_file.txt' -exec cat {} \;
This is a test file.

$
```
I believe the problem is that you haven't found the file yet.

Try this:
```
sudo find /home /root -type f -iname 'sitemanager.xml'
```
Hope it helps. Let us know how it goes.
Regards.

---

