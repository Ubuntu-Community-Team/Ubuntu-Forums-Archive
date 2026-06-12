---
title: "Burn large files accross multiple DVD's"
date: 2009-03-11
forum: General Help
---

### Post by Koobi on 2009-03-11
Hi,
I've been running Ubuntu as my desktop OS since version 5, I think.
I've been upgrading everytime there was a new release. Now, I want to format and reinstall version 8.10

What I don't know how to do is, how to backup a large number of files accross multiple DVD's?
My /home directory is over 12GB. I would like to just drag and drop my home directory into something like GnomeBaker and let it manage the number of files to burn per DVD.

How can I burn 12GB's of data accross multiple DVD's without having to 'tar' and then 'split' the file up into 4.7GB pieces?

Thanks.

---

### Post by klemens on 2009-03-11
why not try to backup on something else as dvd's.
i think an external hd would be much easier or if you don't mind opening you're case just another hd.

but just my 2 cents.

---

### Post by Koobi on 2009-03-11
> **klemens said:**
> why not try to backup on something else as dvd's.
i think an external hd would be much easier or if you don't mind opening you're case just another hd.

but just my 2 cents.

Well, DVD's are my only and only option.

I don't have an external hard disk and they aren't exactly cheap in my country. They are more than twice as expensive as it is in the US, to be exact :)

---

### Post by 3Miro on 2009-03-11
On windows rar had the option to simultaneously compress and split the archive into files. I don't know if anything in Linux would do that, you might have to tar and then manually split the file.

Another thing you might try is start adding files to the tar archive one by one until you reach about 4.7 -> then burn. Basically split the thing into several independent archives, that way if you need just one file, you can do it without swapping DVDs or recombining the big file.

You can also try to burn untarred files to the DVD directly. I have done the latter with CDs when I was baking up my old system before I moved to a newer computer.

---

### Post by dgoosens on 2009-03-11
hi,

you should be able to do this with file-roller
[http://library.gnome.org/users/file-roller/stable/file-roller-creating.html.en]("http://library.gnome.org/users/file-roller/stable/file-roller-creating.html.en")

as you can see here 
[http://library.gnome.org/users/file-roller/stable/file-roller-create-options.html.en]("http://library.gnome.org/users/file-roller/stable/file-roller-create-options.html.en") 
you can specify "split in volumes".

EDIT:
by the way, you could also just leave your home folder as it is if it is on a separate partition and just re-install your /

---

### Post by logos34 on 2009-03-11
> **Koobi said:**
> How can I burn 12GB's of data accross multiple DVD's without having to 'tar' and then 'split' the file up into 4.7GB pieces?

[Kdar]("http://www.debianadmin.com/disk-archive-using-dar-and-kdardar-frontend.html") will divide them up into slices, I think.  But since I don't use Kubuntu desktop and like to keep KDE apps to minimum, I use this handy command to make dvd-size chunks:

> sudo tar czp /home/homebackup$(date +%Y%m%d).tgz  /home/user | split -d -b 4480m - /home/homebackup$(date +%Y%m%d).tgz

You end up with tarred gzipped ~4.7G (4480M) chunks, by date and numbered, i.e. "homebackup20090310.tgz00", "homebackup20090310.tgz01", etc.

good luck

---

### Post by nmgraywiz on 2011-02-11
Greetings Everyone,
     I too am attempting to backup 30GB of files to Multiple DVD's...  I do alot of data recovery, and customers always want them burned to DVD's or CD's...  which for smaller things, is not so bad to just drag until you fill it but it's very time consuming...  I was wondering if any of the options listed had solved the problem for anyone..  I'm going to try them then I'll write back if I found a solution.. I"m sure I"m not the only one out there looking, and it'd be nice to have a solution for those out there who are still looking.. <: -) Thanks everyone for your comments and answers..

L8

The Gray Wizard
(aka: Matthew Romero)

---

### Post by nmgraywiz on 2011-02-12
Greetings Everyone...   

    Ok, here is how I solved the problem...  I tried Diskspan..  can be found here:

[http://sourceforge.net/projects/discspan/files/discspan/discspan-0.2.2/](http://sourceforge.net/projects/discspan/files/discspan/discspan-0.2.2/)

It is not graphical, and I had a few quirks..  It is easy to install by following the readme.  no problem.  

It did not successfully burn to the drive, had trouble with it for some reason, didn't bother troubleshooting after I discovered it had an option to create  direct ISO's to a folder.  Decided to try that option..  When I first tried it, it created one iso which was larger than my DVD size, due to the fact that the file was larger than 2.5GB in size..  so it didn't calculate correctly because it can't break up files.  which is ok, I removed that file, and it generated the mostly correct sizes, with one just slightly over the size.  Decided to use the sizefactor option as .95 (which creates iso's at 95% rather than 100%..  this created ISO's of the correct size I needed...  

Then just burned the ISO's directly using BRASERO..   Life is good..  Thanks to everyone for your suggestions, hope this post helps someone else.  

L8

The Gray Wizard
(aka: Matthew Romero)

---

