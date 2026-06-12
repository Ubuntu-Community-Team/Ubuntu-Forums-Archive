---
title: "Automatically Schedule Ktorrent"
date: 2009-04-03
forum: General Help
---

### Post by eruptionjoojo on 2009-04-03
Hello Everyone ,

           I'm having kubuntu 8.10 on a DELL desktop ...........I want to schedule the ktorrent service to start automatically at a specified time via the inbuilt task scheduler feature in the kubuntu 8.10 ...........
but the problem which i'm facing is as to where is the ktorrent service file(executable one) located on my system ...........because i need to specify the file location in the task scheduler ...........
any help would be greatly appreciated ..........
thnxx in advance ............

---

### Post by eruptionjoojo on 2009-04-03
somebody kindly plese post the pathway as to where the ktorrent executable file is located ................

---

### Post by paradigm2 on 2009-04-03
> **eruptionjoojo said:**
> somebody kindly plese post the pathway as to where the ktorrent executable file is located ................

Probably in /usr/bin or /usr/sbin but I am not sure as I do not have it installed.  What you can do is open up a terminal/shell (Applications -> Accessories -> Terminal in Gnome) and then type

```

whereis ktorrent

```

Check out any directories or paths that it displays.

---

### Post by eruptionjoojo on 2009-04-04
Thnxx a lot for your reply ..............
and yeah i did try to schedule Ktorrent using the above mentioned pathway i.e. /home/usr/bin/Ktorrent ............. but then no use as such while the scheduled task runs automatically nothing happens i mean the ktorrent service doesn't start ......... but in order to find out what was actually happening i ran the task using the "run now" feature in the task scheduler ............
then i found that the ktorrent service was getting started but then as soon as the execution was completed the ktorrent service exited i.e as soon as i closed the bash window manually .......... 
                    but,then while the task gets executed automatically the execution takes place at the back i.e. the bash window doesn't appear thus it seemed as if nothing was happening .........
I want to schedule the task of ktorrent service to start auotamtically at a specified time ....... via inbuilt task scheduler or any other way ............
any help would be greatly appreciated ........
thnxx in advance .......

---

### Post by eruptionjoojo on 2009-04-04
somebody please tell me how to schedule the ktorrent task ............... please

---

### Post by eruptionjoojo on 2009-04-04
Bump ................

---

### Post by eruptionjoojo on 2009-04-04
please guide me as to how to do it ............. BUMP

---

### Post by mister_p_1998 on 2009-04-04
Its not in /Home/usr/bin
its  /usr/bin/ktorrent

if you schedule in cron, you need to enter the line  

00 04 * * * export DISPLAY=:0 && /usr/bin/ktorrent
 this will run ktorrent at 4:00am every day of every month

if you dont put the export DISPLAY=:0 it will still run but you wont see anything onscreen.

Steve

---

### Post by eruptionjoojo on 2009-04-05
> **mister_p_1998 said:**
> Its not in /Home/usr/bin
its  /usr/bin/ktorrent

if you schedule in cron, you need to enter the line  

00 04 * * * export DISPLAY=:0 && /usr/bin/ktorrent
 this will run ktorrent at 4:00am every day of every month

if you dont put the export DISPLAY=:0 it will still run but you wont see anything onscreen.

Steve

Thnxx a lot for your reply steve .............
but while i try to save this new entry in the Crontab i'm not able to ........
infact i don't know how to .......... so kindly please guide me as to how to save the new entry in the Crontab .............
thnxx in advance .........

---

### Post by eruptionjoojo on 2009-04-05
commom guys please tell me how to save the crontab new entry in kubuntu ...........
please ..........

---

### Post by eruptionjoojo on 2009-04-05
Someone please help me ............... BUMP

---

### Post by eruptionjoojo on 2009-04-05
:lolflag: Bump ............ Bump :lolflag:

---

### Post by eruptionjoojo on 2009-04-05
Please tell me how to do it ................ i'm still waiting for a reply .........

---

### Post by mister_p_1998 on 2009-04-06
you need to type crontab -e
to create a new cron for your username, or to edit a current one

Heres mine:

# m h  dom mon dow   command
35,45 08 * * 1-5 DISPLAY=:0 && /usr/bin/audacious /home/steve/Desktop/rp_128.m3u
0 * * * * /usr/bin/get_iplayer --pvr 2>>/tmp/get_iplayer.log
45 08 * * 6,7 DISPLAY=:0 && /usr/bin/miro
00 18 * * 1-5 DISPLAY=:0 && /usr/bin/ktorrent

This will run ktorrent at 18:00 Monday to Friday
you might want to also setup the Ktorrent internal scheduler to start & stop at a certain time.
Steve

---

### Post by eruptionjoojo on 2009-04-06
> **mister_p_1998 said:**
> you need to type crontab -e
to create a new cron for your username, or to edit a current one

Heres mine:

# m h  dom mon dow   command
35,45 08 * * 1-5 DISPLAY=:0 && /usr/bin/audacious /home/steve/Desktop/rp_128.m3u
0 * * * * /usr/bin/get_iplayer --pvr 2>>/tmp/get_iplayer.log
45 08 * * 6,7 DISPLAY=:0 && /usr/bin/miro
00 18 * * 1-5 DISPLAY=:0 && /usr/bin/ktorrent

This will run ktorrent at 18:00 Monday to Friday
you might want to also setup the Ktorrent internal scheduler to start & stop at a certain time.
Steve

thnxx a lot for your reply steve ...........
but while i try to save the crontab new entry i'm not able to .......... wuld you please tell me how to save the new entry ..........


infact while i type the command in the terminal i get the following :-
joojo@ubuntu:~$crontab -e
 
                  the output to this is that the crontab gets opened then it displays this :-
# File generated by KCron the Saturday 04 April 2009 10:21.




and the bottom of the window a line is displayed as :-

"/tmp/crontab.UKt9VE/crontab" 2L, 61C


but i can only type by pressing I first because it enables the insert function but then not able to save it .........






thnxx in advance .........

---

### Post by mister_p_1998 on 2009-04-06
After you've edited your new crontab, do CTRL X
then S then ENTER (to save)
thats it.

Steve

---

### Post by kpkeerthi on 2009-04-06
> **eruptionjoojo said:**
> thnxx a lot for your reply steve ...........
but while i try to save the crontab new entry i'm not able to .......... wuld you please tell me how to save the new entry ..........


infact while i type the command in the terminal i get the following :-
joojo@ubuntu:~$crontab -e
 
                  the output to this is that the crontab gets opened then it displays this :-
# File generated by KCron the Saturday 04 April 2009 10:21.




and the bottom of the window a line is displayed as :-

"/tmp/crontab.UKt9VE/crontab" 2L, 61C


but i can only type by pressing I first because it enables the insert function but then not able to save it .........






thnxx in advance .........
It appears that you have vi/vim as your default system editor. You could change that to kwrite or kate (or any other graphical editor) but changing the "EDITOR" environment variable. 

You do this by running the following command:
```

sudo update-alternatives --config editor

```
and then choose kwrite or kate from the list. Now try ```
crontab -e
```

Note: You may want to logout and log back in for the settings to take effect.

Also see [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by eruptionjoojo on 2009-04-06
> **kpkeerthi said:**
> It appears that you have vi/vim as your default system editor. You could change that to kwrite or kate (or any other graphical editor) but changing the "EDITOR" environment variable. 

You do this by running the following command:
```

sudo update-alternatives --config editor

```
and then choose kwrite or kate from the list. Now try ```
crontab -e
```

Note: You may want to logout and log back in for the settings to take effect.

Also see [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
thnxx a lot for your reply ............
but the options are as follows and do not include Kate or Kwrite etc .

There are 3 alternatives which provide `editor'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/vim.tiny
          2    /bin/ed
*+        3    /bin/nano

Press enter to keep the default[*], or type selection number:


please guide me how to do it ...........
thnxx in advance ...........

---

### Post by eruptionjoojo on 2009-04-06
> **mister_p_1998 said:**
> After you've edited your new crontab, do CTRL X
then S then ENTER (to save)
thats it.

Steve

thnxx again for your reply but i'm really confused as to how to save it . i will tell exactly how i do it and what happens accordingly :-

Steps:-

joojo@ubuntu:~$crontab -e(this is what i enter in the terminal)

                  the cron tab window gets opened by this . the window contains two lines basically one being at the top of the window as :-

# File generated by KCron the Saturday 04 April 2009 10:21.


and the second one being at the bottom as:-

"/tmp/crontab.P9r9xd/crontab" 2L, 61C


but till now i'm not able to type anything until and unless i press the I key and a sign at the lower left corner of the window appears saying INSERT .......... after this i'm able to type in the window but then after making the new entry i press CTRL+X this displays (^X)symbol in blue next to the new entry and thn press s but nothing gets saved ...........
please help me as to i'm really a n00b ............
thnxx in advance ..........

---

### Post by eruptionjoojo on 2009-04-06
After reading how to change my editor using a command i changed the editor by typing the following command in the terminal :-

export EDITOR=kate

But then while i type :-

sudo crontab -e

the kate text editor is not used for editing rather the original text editor (i mean the basic one ........ i don't know which one it is i guess nano or vim etc.) is used ............
while on the contrary while i type the following(in the terminal) the Kate editor is used :-

crontab -e


the kate text editor is used ............ why this is so .............
kindly help ............... i'm really frustrated by this ..............
thnxx in advance ...........

---

### Post by kpkeerthi on 2009-04-06
Use 'crontab -e' and put your cron command in there. This would be the logged in user's crontab.

If you use 'sudo crontab -e', you would end up seeing super-user's crontab which obviously is not the right place to put ktorrent.

You may want to put the export command in your ~/.bashrc (or .profile) file. If you want to have it system-wide put the export command in /etc/profile.

---

### Post by mister_p_1998 on 2009-04-06
ok try this:
sudo kate /var/spool/cron/crontabs/yourusername

then type or paste your cron stuff into this file and save it

Be Careful! this is not a safe way to do this!
Steve

---

### Post by eruptionjoojo on 2009-04-06
> **kpkeerthi said:**
> Use 'crontab -e' and put your cron command in there. This would be the logged in user's crontab.

If you use 'sudo crontab -e', you would end up seeing super-user's crontab which obviously is not the right place to put ktorrent.

You may want to put the export command in your ~/.bashrc (or .profile) file. If you want to have it system-wide put the export command in /etc/profile.

Yeah i'm doing that only i mean putting the new entry into the crontab window (after having typed in the terminal the command :- crontab -e )
but then i'm not able to save the new entry ............. that's what the problem is .................

---

### Post by eruptionjoojo on 2009-04-06
> **mister_p_1998 said:**
> ok try this:
sudo kate /var/spool/cron/crontabs/yourusername

then type or paste your cron stuff into this file and save it

Be Careful! this is not a safe way to do this!
Steve

thnxx a lot for your reply - steve 

but then i ran the command in the terminal and the output was as follows :-

joojo@ubuntu:~$ sudo kate /var/spool/cron/crontabs/joojo
[sudo] password for joojo:                                
Error: "/var/tmp/kdecache-joojo" is owned by uid 1000 instead of uid 0.
kate(6157): createDoc                                                    
kate(6157) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/joojo/.kde/share/apps/kate/sessions"                                                                              
kate(6157) KateApp::initKate: Setting KATE_PID: ' 6157 '                                         
Error: "/tmp/kde-joojo" is owned by uid 1000 instead of uid 0.                                 
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: false                                  
kate(6157) KateMainWindow::KateMainWindow: **************************************************************************** 0x9529648                                                                 
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: false                                  
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: false                                  
kate(6157) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"                                                                                                
kate(6157) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "joojo"
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: false                                  
kate(6157) KateApp::startupKate: KateApplication::init finished successful                       
Error: "/tmp/ksocket-joojo" is owned by uid 1000 instead of uid 0.                             
kate(6157) KToolInvocation::klauncher: klauncher not running... launching kdeinit                
Error: "/tmp/kde-joojo" is owned by uid 1000 instead of uid 0.                                 
Error: "/tmp/ksocket-joojo" is owned by uid 1000 instead of uid 0.                             
kdeinit4: Shutting down running client.                                                          
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher                                    
Error: "/tmp/ksocket-joojo" is owned by uid 1000 instead of uid 0.                             
Error: "/tmp/kde-joojo" is owned by uid 1000 instead of uid 0.                                 
kdeinit4: preparing to launch /usr/bin/kded4                                                     
Error: "/var/tmp/kdecache-joojo" is owned by uid 1000 instead of uid 0.                        
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4                                             
kbuildsycoca4 running...                                                                         
Error: "/var/tmp/kdecache-joojo" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-joojo" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: true
kate(6157) KateDocManager::slotModChanged1: KateDocManager::slotModChanged (1)
kate(6157) KateDocManager::slotModChanged1: KateDocManager::slotModChanged (2)
kate(6157) KateViewDocumentProxyModel::updateBackgrounds: true
kate(6157) KateDocManager::slotModChanged1: KateDocManager::slotModChanged (1)
kate(6157) KateDocManager::slotModChanged1: KateDocManager::slotModChanged (2)
QThreadStorage: Thread 0x93aaf80 exited after QThreadStorage 2147483643 destroyed


and the kate text editor which got opened showed the following :-

# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.kSwBfD/crontab installed on Mon Apr  6 15:59:35 2009)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)

# File generated by KCron the Saturday 04 April 2009 10:21.


                 after this i added the new entry and pressed save ............ the new entry did get saved but nothing happened at the scheduled time ............ don't know where did i get it wrong .........
the new entry which i had added was this :-

35 18 * * * export DISPLAY=:0 && /usr/bin/ktorrent

please guide me as what else needs to be done in order to make it work ........
thnxx in advance ...........

---

### Post by eruptionjoojo on 2009-04-06
Bump ............. Bump ............ Bump :lolflag:

---

### Post by eruptionjoojo on 2009-04-06
Bump .............

---

### Post by eruptionjoojo on 2009-04-06
thnxxx a lot everyone for your contribution ...............
i finally got it done .............. scheduling it using the inbuilt task scheduler which could be reached at the following :-
System Settings->Advanced->Task Scheduler.
though i'm still not able to do it the manual way ............. still don't know how to save it in the manual way ............
thnxx again everyone .............

---

### Post by mister_p_1998 on 2009-04-06
Did the schedule go off ok?
All the bumps are more than a little annoying!
people have jobs and lives outside this forum, please show a little respect and have patience.
Steve

---

### Post by eruptionjoojo on 2009-04-07
> **mister_p_1998 said:**
> Did the schedule go off ok?
All the bumps are more than a little annoying!
people have jobs and lives outside this forum, please show a little respect and have patience.
Steve

thnxx a lot for your reply ...........
and yeah somewhat sorry for Bumping it all the way ............
anyways yeah it works fine with the inbuilt task scheduler of kubuntu by scheduling it to display the window as well using the command :-
kstart --type Toolbar --window Cron --display :0 /usr/bin/ktorrent 
(got this command from another forum)
though i tried this script as well :-
export DISPLAY=:0 && /usr/bin/ktorrent
but since it was not an executable one it didn't work ............ 
but don't no why till now i'm not been able to do it the manual way .........

---

