---
title: "How to 'see' files run on XP system"
date: 2010-07-03
forum: Desktop Environments
---

### Post by explore on 2010-07-03
I have downloaded and run Ubunto and want to run this system on the same computer that has up until today only had Windows XP running. How can I get my programs and my files to show up in Ubunto. 

I have noticed on one thread that Samba may let Umbunto 'see' the files in XP.  

I have down loaded  Samba but it says that Windows does not recognize the program. The 'unzipper' programs are all for fee. ARe there any free?

Do I need to download Samba while running Ubunto to transfer the files and programs to Ubunto?

--Explore

---

### Post by wookieshaver on 2010-07-04
Ok, to answer your first question: Yes, there are free unzipping utilities. 7-Zip is freely available here:
 
[http://download.cnet.com/7-Zip/3000-2250_4-10045185.html](http://download.cnet.com/7-Zip/3000-2250_4-10045185.html)
 
Ubuntu by default has the samba program installed in all the versions I've used. You need merely to go to "places" from the menu bar and you will see the XP partition listed there. Click on it and it mounts and voila you can see all the files on the XP partition of your drive.
 
As to the programs you use in Windows XP, its a little different. OpenOffice is the default office program that comes free (like most linux software) with Ubuntu installs. That will take care of your need to view, edit or create Microsoft Office type documents. As for the rest, I would check this guide out to make Ubuntu comfortable to use after you install it:
 
[FONT=Calibri][http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html](http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html)[/FONT]
 
[FONT=Calibri]These simple steps make Ubuntu a lot more user-friendly if your just now making the transition from Windows or running it side by side with Windows.[/FONT]
 
[FONT=Calibri]Enjoy![/FONT]

---

### Post by Morbius1 on 2010-07-04
wookieshaver, you're a better man(?) than I am.
>  I have downloaded and run Ubunto and want to run this system on the same  computer that has up until today only had Windows XP running. How can I  get my programs and my files to show up in Ubunto. I interpreted this as "I'm dual booting WInXP with Ubuntu, how can I access my WinXP files"
>  I have noticed on one thread that Samba may let Umbunto 'see' the files  in XP.  It's the other way around. Samba itself allows XP to see folders you have set to share on your Ubuntu machine. But only if that XP machine is on another box in your home network. Not if it's a dual boot.
>  I have down loaded  Samba but it says that Windows does not recognize  the program. The 'unzipper' programs are all for fee. ARe there any  free?If you're going to install Samba it has to go on Ubuntu not windows.
>  Do I need to download Samba while running Ubunto to transfer the files  and programs to Ubunto?I'm lost completely on that one.

Please tell us if you have WinXP and Ubuntu installed on the same box.
And if it is on the same box, how did you install it? Separate partition or through Wubi ( Installed within Windows? )

---

### Post by explore on 2010-07-04
@Morbius1   
I down loaded Ubunto while surfing the web in XP. Then I ran the the down loaded file and  installed. Then the machine shut down and restarted at which point a screen appeared with the option of booting with XP or Ubunto.  I think I allocated 17 Gigabytes for Ubunto, but I can not recall. I think I under allocated space for the program. How can I find the space allocated for Ubunto on my  computer?   Perhaps it would be wise to uninstall and then reinstall and allocate a large portion of the hard drive to the new Operating system Ubunto because I like it so far.    

This new Ubunto program I am running is running on my only computer So when I use Ubunto, I have to make a choice to boot with Ubunto at a critical moment in the boot process.  

I believe I partitioned the hard drive because I did not use Wubi.

My objective is to transfer my files to the new operating system of Ubunto and then leave Windows permanently.  I need to be able to get 5 years of data or 45 gigabytes of data to be seen by the new Ubunto system.

I hope this additional information helps to determine the solution.


P.S. Thank you folks for taking the time to respond to my issue.  :D

---

### Post by Morbius1 on 2010-07-04
> I down loaded Ubunto while surfing the web in XP. Then I ran the the  down loaded file and  installed. Then the machine shut down and  restarted at which point a screen appeared with the option of booting  with XP or Ubunto.I know very little about Wubi but based on that description I fairly certain you used Wubi. If I'm correct then your windows partition can be found here: **/host** when you boot into Ubuntu..

[COLOR=Blue]EDIT: Actually I guess they could also be in **/media**:[/COLOR]
From: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
> 
Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.


---

### Post by KdotJ on 2010-07-04
Ubuntu*

---

### Post by explore on 2010-07-04
I am a complete newbie in this Ubunto issue, 

I found them!  At least most of them. I am missing some Itunes music ( 8 gigabytes). But I plugged in the Ipod and it played!  It played the movies and songs!  

Now my question is about security issues.
I could not run the Soft ware when I clicked on the link. The ending was .Ink and it asked me what program to use to open the file and I did not know which one so I did not try.

Also
I want anonymous surfing,
Anti virus program. I have Kaspersky on XP side.
I like spy ware Doctor on XP

and I was running peer block also.

Oh, and carbonite is useful on line back up. 

I also like my  ApC Powerchute battery Back up  for graceful shutdown after AC power outage..
I also like Getgo for capturing youtube videos for archiving. 

This is so exciting! I have long dreamed of escaping the tyranny of William (Bill) Gates!


Thank you so much for all your help so far!  This is quite an exciting experience  in new waters for me!...  :D

---

### Post by Morbius1 on 2010-07-04
Each on of your questions is a separate thread in itself.

Let me take the easy one:
> I could not run the Soft ware when I clicked on the link. The ending was  .Ink and it asked me what program to use to open the file and I did not  know which one so I did not try.You aren't going to be able to run any windows "lnk" shortcuts or any windows *.exe either. There's the linux world and there's the Windows world. You can open up text files, open office files and such but you won't be able to open or execute any Windows specific program or utility.

---

### Post by explore on 2010-07-05
I guess now that I have the "files" issue solved I want to know  how to run the Anon type programs. I am looking into Tor, but there appears to be many settings I don't know how to adjust to get it to work.

---

### Post by explore on 2010-07-06
I am now going to end this thread and start one more directly related to my current objective.

---

