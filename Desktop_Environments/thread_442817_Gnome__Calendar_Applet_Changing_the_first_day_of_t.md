---
title: "Gnome:  Calendar Applet: Changing the first day of the week to be Monday"
date: 2007-05-13
forum: Desktop Environments
---

### Post by tinker123 on 2007-05-13
The Calendar applet in Gnome used to give the ability to the user to change the first day of the week.   That ability was taken away and the Calendar applet now reads this information from the locale file for your country.

If you don't like the first day of the week being Sunday, as is my case you have to hack the file.

Here is how I did it.

I found this HowTo written for Gentoo by someone living in Great Britain (GB) who wanted to change the first day of the week from Saturday to Monday:

[http://gentoo-wiki.com/HOWTO_localedef](http://gentoo-wiki.com/HOWTO_localedef)

I am using Ubuntu 6.10,  I live on the east coast of the US,  and I wanted to change the first day of the week from Sunday to Monday.  

You should read and understand that short HowTo because I am not expert and you will want to adjust the directions to your situation.

Let me write that again as it is important

You should read that short HowTo because I am not expert and you will want to adjust the directions to your situation.

Okay, here goes the abbreviated version for east coast American Ubuntu 6.10 users who want the first day of the week to be Monday in the Calendar Applet:

1.  From your home directory fire up a terminal, log in as root:

sudo bash

2. Make a copy of your locale file in your home directory
cp  /usr/share/i18n/locales/en_US  en_US_modified

3. create a directory "locales"
mkdir locale

4.  open up en_US_modified in an editor,  search for the section called "LC_TIME"

5. look for the line

first_weekday 1

6.  Change the 1 to a 2

7.  Save the file, exit your editor and go back to the terminal

8.  Run this command which will create a directory full of new locale settings inside of the "locale" directory you made in your home directory:

localedef -c -i en_US_modified -f UTF-8 locale/en_US.utf8

9.  Backup your old locale settings by going to   /usr/lib/locale and changing the name of

en_US.utf8 

to
en_US.utf8_ORIGINAL

10.  Copy the new  en_US.utf8 directory your created in your home directory in the subdir "locales" to 
 /usr/lib/locale

11.  Restart your system

Don't skimp on the backups or on making sure you understand the howto quoted above.   I barely understand what I am doing.   You are taking a risk by following these directions.

Good Luck

---

