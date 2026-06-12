---
title: "K-12 school systems."
date: 2007-06-30
forum: Education &amp; Science
---

### Post by itzpapalotl on 2007-06-30
Hey all. First off. I'd just like to say that Ubuntu, and this community are just the coolest. 
I'm a recovering Windows admin at a small school, whose main governing philosophy is one of open communication, sharing of information, democracy and cooperation. So... open source really. But... we are running exclusively MACrosoft.
My job over this summer is  to make our system line up with our philosophy. A full open source conversion. (where possible). Mostly this means Ubuntu. 
I'm opening up this thread with the following questions:
Anybody out there already running a fully open source K-12, and if so; What software are you using for school administration end of things? I have been looking at Focus-SIS, but I'd like to hear from some folks.

Next: Edubuntu... I'm not going to be using thin clients, are there any other major advantages I should be considering?

Thirdly: open source internet content filtering? I'm looking at A SQUID proxy with some nanny program, but where can I get an updated no no list from?  I don't mind paying for the service, but again I'd love to hear from some folks who are actually using these things before I make my decisions.

Lastly (for now): High-school level educational packages. There is a ton of stuff out there for the little ones, but I'm having less luck finding packages for higher level students.  

Thanks in advance all. I know these questions are vague in places, but I REALLY want to make this work,so any suggestions and help will not be turned away. Pile on the links. 
I'll read a thousand pages if I need to. 

Thanks again
Itzpapalotl
Freaked Out Linux Newbie On A Mission.
California, USA.
;)

---

### Post by cprofitt on 2007-07-02
itz:

If you can keep me posted on the progress of your conversion.

I am a Windows admin at a K-12 district as well... and my district still refuses to consider the switch. Certainly at K-12 volume pricing it is hard to justify (read: $54 per license for Windows and .35 per user cal) on price alone.

The hurdles I foresee are:

[LIST]
[*]Mass image deployment - what replaces SYSPREP, GHOST, BDD?
[*]Ability to change user settings (OS and specific application) via LDAP logon - Think AD GPO or ZenWorks from Netware
[*]The ability to have clustered file servers (built-in to Server 2003 Enterprise)
[*]The ability to limit user storage space (not sure if the tools are there)
[*]The ability to limit the types of files stored in user home directories (no executables)
[*]The ability to generate reports on file storage usage
[*]Replacement for student information system -- though the application is web based so that may not be an issue (it runs on server 2003/SQL)
[*]retraining the development team (oh, that would be me) which currently uses .Net for creating just-in-time applications
[*]What email server would replace Exchange 2007 and its features?
[*]retraining staff to use Open Office (and any other replaced applications)
[/LIST]

That is just off the top of my head... I am sure that there are more concerns (hurdles) to jump. I am working through some of the issues on my home computers as well... though I have my daughter converted and she is loving Ubuntu.

---

### Post by yochaigal on 2007-07-02
hey i work for a IT firm (that's a worker-coop) and we're doing an upgrade for a pre-existing linux lab at a middle school in san francisco.  
a few things i've noticed in terms of hurdles---
if you aren't using thin-clients, you just saved yourself a lot of trouble but not a lot of money.  thin clients can be 10 year old diskless ghosts but still give quite an impression when they are running open office and firefox like nothing.  the real problem is getting them to network boot without a floppy, which basically comes down to buying PXE enabled NICs. 
good idea with squid.
backuppc is good.
a moodle server for multimedia.
and zabbix.  check 'em out if you haven't already.

---

### Post by cprofitt on 2007-07-02
Moodle for multi-media?

I think of Moodle as more of a class-room discussion/assignment board. Sharepoint has better features than Moodle, but costs too much.

---

### Post by itzpapalotl on 2007-07-02
PrivateVoid. Ofcourse I'll keep people posted, frankly as matter of pure necessity. Now. to be honest, I'm dealing small scale here. Not trying to convert an already functioning district. BUT, many thing swill apply. Also I'm dealing with a broken system. We are operating on nothing newer than 5 years old with the exception of a few office computers and my laptop (currently running Feisty with Beryl like a dream) We have only a handful of working internet connections in the building, and next year 300 students are going to walk through the doors.

My charge:
 Get the internet in to every room. Get a machine in there to use it. Get a computer lab up and running. Get a student information system that isn't Samantha god love her.. Get a proper presentation room set up in the Main Hall, Get a new machine up and running in all of the 21 administrators offices, get it all centralized and do it for $30,000 (a donation). 
I had last year to plan it, I have this year to do it. 

[B]
    * Mass image deployment - what replaces SYSPREP, GHOST, BDD?[/B]

Im my case, this first time around, not happening unless I learn something new in the next few weeks. . I'm dealing with a sum total of 80 computers, most of which are essentially identical (and most of which I just plain don't have yet.), so yeah image deployment would make things much easier. I'll get back.

   ** * Ability to change user settings (OS and specific application) via LDAP logon - Think AD GPO or ZenWorks:**
Well, once I figure out what is bugging the new server, and why it wont update properly, (not generally a problem with windows, I'll grant you) I'll be installing OpenLdap and some front end stuff I'ver been researching, which I think brings me up to  par with Server 2000 (our current beast) at the very least. 
[B]
    * The ability to have clustered file servers (built-in to Server 2003 Enterprise)[/B]
Clusters? like parallel processing clusters.. way over my head. As for file servers, Looking to have the big guy handle that with it's 700+ gigs of storage, Via NFS. That will be backed up nightly via chron job to a Buffalo terastation, and the whole thing is set up RAID 5 with Logical Volume Management on top, so if I need more disk, I put in more disk. 


**    * The ability to limit user storage space (not sure if the tools are there)**
I feel certain that they are, but I can't tell you WHAT they are just yet.. (oh yeah... in WAY over my head here (And loving it))
[B]
    * The ability to limit the types of files stored in user home directories (no executables) [/B]

I think that's just plain old built in to Posix in general, but applying 666 permissions (I think it's 666) to new users shouldn't be too tough. Then even if they manage to get an executable file on to the drive, they won't actually be able to execute it. 
[B]
    * The ability to generate reports on file storage usage[/B]

I my case I think "no need" is the answer, but I'll look in to it.

   ** * Replacement for student information system -- though the application is web based so that may not be an issue (it runs on server 2003/SQL)**

Ah yes. Samantha. The finest student information system ever created. My guess is that nothing I deploy will compare, but it does bring us round to one of my first questions. Focus-SIS or OpenAdmin. Right now I leaning heavily Focus-SIS, but have yet to find anybody actually using it who will call me back. ;-)

 **   * retraining the development team (oh, that would be me) which currently uses .Net for creating just-in-time applications.**
     This Community, the Ubuntu Book, Google, and a strong desire to make this work. As far as development team, yeah. Me, and to be honest I'm in way over my head, but the worst case scenario is baling out in total failure and relying for an additional year on the system we have, plus the new computer lab,  which  I suppose I can put the old Wink2kPro back on. 

 **   * What email server would replace Exchange 2007 and its features?**

Ah, and here you have me. We currently do not use Exchange server, but we needs MUST use something like it, with reference to the email problems above. Come On RoloDAP development team. Otherwise I am content to use the management system built in to Focus-SIS to handle student parent contacts for now, but I mean. If I really actually knew what Exchange did...

**    * retraining staff to use Open Office (and any other replaced applications)**

I know this sounds snide, but I'm having plenty of trouble getting them to work with the few Microsoft office systems we have, so training everybody from square one at the same time sounds like a breath of fresh air to me. Besides, with the exception of some advanced mathematical stuff in excel, for our purposes it ports pretty well. 

Once I have my website up and running, I detail this whole operation as it happens there. For now... Ack. Just wish me luck I guess.

Itzpapalotl.
Still Freaked Out, Still On A Mission.

---

### Post by cprofitt on 2007-07-03
Sounds like your situation is much different than mine.

My environment has roughly 6000 students (currently using AD - in the past we were a Netware shop) coupled with roughly 1000 faculty and staff. We currently are running an EVA 4000 with roughly 8tb of data capacity.

**Clusters**:
Microsoft File clusters are actually one live, one spare scenarios that create a virtual server name that serves the files. The attached storage would have to be visible on two (or more) servers so that they could both see the disks. When the controlling server goes down the spare server starts the virtual server and takes control of the disks all in a matter of 5-10 seconds. Before I could take my file servers off of Microsoft I would need similar functionality. Novell offered similar clustering with Netware 6, but I am not sure what they provide now.

**Exchange Server**
The features of Exchange 2007 that would potentially be important for a K-12 district would be mail box size limits, the ability to have multiple mailbox servers in the same domain (one for faculty/staff and another for students), the ability to have email automatically scanned for content (checking student mail for threats, etc or scanning administrative emails for "keywords" that need to be retained for legal reasons), an edge transport server which sits in the DMZ limiting the exposure of the rest of your system to attack. Depending on the tech savvy level of your administrators it also comes in with built-in services to sync with mobile phones, clear data from lost mobile phones, and do voice activated calendar processing.  If you school is considering moving to a VOIP solution Exchange 2007 offers a tie in to your existing PBX.

**Student Information System**:
We are actually moving from Chancery to Infinite Campus.

**Generate Reports on File Storage Usage**:
We have departmental budgets so we have a need to ensure people pay for their "disk space" and reports will help you quickly show administrators if there is a rampant problem with students storing material they should not be.

Feel free to message me privately if you need help/advice -- are you in the USA?

---

### Post by amoore on 2007-07-03
> **PrivateVoid said:**
> Moodle for multi-media?

I think of Moodle as more of a class-room discussion/assignment board. Sharepoint has better features than Moodle, but costs too much.

I wish more schools used Moddle. Black board and WebCT are crappy CMS's.

---

### Post by izizzle on 2007-07-04
As an 8th grade middle school student, I am very touched by the efforts of itz's school. I think that they are making a great decision to switch to open source software and I admire their philosophy greatly. In my opinion, you may want to start out with edubuntu, so the kids get used to it, then gradually move up to ubuntu. Another way is to start out with KDE, just because it has a Windows-like feel to it, and then move up to ubuntu.  As for my school.....well what can I say. The computer teacher is such a windows n00b, that he thinks that the Ubuntu servers actually run Windows. How crazy is that???? I mean seriously, are you*** really*** thinking that? Anyways, I hope you have a great experience at you school with whatever distro you choose to start out with, and, **MAY THE UBUNTU BE WITH YOU!!**

---

### Post by itzpapalotl on 2007-07-05
Rogh ride so far gang.. Managed to Bork the LAMP server, and am moving rapidly backwards!! Yay. I'm staring at ablue screen of nothing waiting...
But
I have my project outline up on my website, so rather than fill this thread with twelve pages of project outline.. for those interested in what's up.

[http://www.r3dstonecreative.com/linarchist](http://www.r3dstonecreative.com/linarchist) will get you my home page. It aint pretty, and right now it's just the project outline. 

I'll be updating it regularly from here on in, and posting to this thread as the action unfolds... Or as is the case right now... fails to unfold.

Ohh Ohh. instant update... The Blue Screen Of Nothing is gone, and I am being asked to throw on the base system. It was one of the SATA drives. Thankfully I had another floating around.

BTW thanks Izizzle. It's nice to hear from the kind of people who will actually be USING this system. In response, I'm not using edubuntu, but I will have KDE on many of the systems. I know that Windows users find KDE more comfortabe. The staff will get KDE if they want it. The students in general,l especially the younger ones... They are just plain adaptable, and seem to not even notice that this computer is Linux, and that one is Windows. Get 'em on the web, let 'em type up some Homework, and well.. they are happy. Give 'em Beryl and they think they are kings of cyber-space, and that's fine, because they are...

Anyhoo. I'll be taking the brunt of my updates on this project to my website. Feel free to look around at it. I'll post a web form for feedback at some point, but ah... right now I'm buried up tio the elbows in PostgreSQL issues. 
More Soon.

Itzpaplotl.
A little less Freaked out now that the LAMP has been turned on. But STILL ON A MISSION!!!

---

### Post by itzpapalotl on 2007-07-25
Okay. Been a while in updating. Things went a little haywire at the school. Lots of construction, and the computer lab has been cut in half... But there is still plenty of room. I had to spend a week moving the network lines, and dealing with a broken copier.

So. Conversion is going very well.

The Lamp server as I said is running, and now has all of its installs operational. 
We have chosen Focus-sis as our student information system, and because of the people here at the forum, I have a rudimentary install of Moodle up and running. I had no idea. It neatly answers Angel Learning, and the documentation is fantastic. 

If I had one wish, it would be for Focus-SIS to have the kind of docs that Moodle has. 
Focus has largely been a headache to get configured, but I had counted on that. For the most part we have had to enter all of our data by hand. Not a big deal in a school of our size, but a bit time consuming. We now have a functioning student information system which will be handling our grading, behavior, extracurricular elegebility and attendance. At this point A group of administrators are hard at work entering the student population. We still haven;t worked out how we are going to deal with historical records yet. It has something to do with exporting from Chancery Winschool (proprietary), to ASCII to CSV to PostgreSQL, and I am just NOT a database expert, but we'll get there. For now we are choosing to just get up and running. 
Master schedule is in, and classes will be populated based on a schedule that has already been worked out.

Moodle is not a system that I am directly involved with on anything other than a keep it running level. Apparently one of our staff has some expirience with these things, and so I happily deligated the task away. I hadn;t figured on configuring another system. I have no doubt that Moodle is going to revolutionize how we run our school. 

We are actually getting very close to having our central systems fully running. 

On the front end I have had quite a bit of trouble getting the firewall / Network Address Translator working. Part of the problem is that that I have to keep things running for most of the day so I can only try to swap the system over for an hour or so at then end of the day. 

Iptables is a complex mess. Looking for descent firewall builder front end to help me along. Squid I think will be cake, but I haven't gotten there yet. Any help with this would be appreciated.

I do have half of the school set up with wireless, having chosen to go to an entirely wireless network structure on campus. I'm using our current wired network, as a spine for 11 access points, and going from there to 4 port wireless Ethernet bridges and back to plain old Ethernet. It turns out to be far less expensive than dropping lines in all the rooms that don't have them. I should be done with the whole network by the end of the week. 

I now have a fleet of nine very nice classroom computers all running an out of the box Dapper. I have not connected them to the wireless network yet. I am still trying to wrap my head around how the network will finally look. I have a few problems. The first is that the 192.168 class C network is no longer adequate. It really never was. I am needing to switch to a class B at least, but frankly I might as well get used to the ten dot stuff. Now:

System Machines: 10.0.0.x (Static IP)
Classroom machines: 10.0.1.x (Static IP)
Staff machines: 10.0.2.x (Static IP)
Computer Lab 10.0.3.x (Static IP)
Student lap tops (via wireless) 10.0.4.x (DHCP with 1 hour lease)

That is the plan. so...
Subnet mask is..
255.255.0.0 yes but I'm not really making a subnet right? just one big network with 65000 available ports rather than just 250 yes?

I want a firewall at 10.0.0.0
a Squid / openLDAP / router thingy at 10.0.0.1
My LAMP at 10.0.0.2
Some Kind of NFS server at 10.0.0.3
A buffalo Terastation NASC for backup at 10.0.0.4 (This thing is giving me nightmares)
The access points starting at  .0.100 and going to .0.111
I don't think the bridges need IPs but if they do, then they get .200 through .220

That's all fine, but how the heck do I do DHCP for the student laptops?

Our current network is a nightmare. I really just don't know what the guy was thinking. I get address conflicts all over the place. Looking in to it I have both server 2000 AND the sonicwall unit serving DHCP, as well as a number of devices that reserve their own IP address without telling anybody. I REALLY need to get this new network gateway thing solved. It's holding up the show. OpenLDAP is a bit mysterious on its own. Anybody know some good front end stuff?

Till next time

---

### Post by UbuWu on 2007-07-25
> **itzpapalotl said:**
> 
[B]
    * Mass image deployment - what replaces SYSPREP, GHOST, BDD?[/B]


[SystemImager]("http://wiki.systemimager.org/") might be helpful here.

---

### Post by itzpapalotl on 2007-07-25
Ahhhhh.......
Hallelujah! An automated image deployment system! Lots of image deployment wares out there. Most require some babysitting. I'm going to check this out! thank you!

---

### Post by UbuWu on 2007-08-06
[Clonezilla]("http://clonezilla.sourceforge.net/") looks even better:

> Clonezilla, based on DRBL, Partition Image, ntfsclone, and udpcast, allows you can massively clone many (40 plus!) computers simultaneously. Unlike G4U (Ghost for Unix) or G4L (Ghost for Linux), Clonezilla saves and restores only used blocks in the harddisk. This increases the clone effiency. At the NCHC's Classroom C, Clonezilla was used to clone 41 computers simultaneously. It took about 50 minutes to clone a 5.6 GBytes system image to all 41 computers via unicasting and only about 10 minutes via multicasting!

---

### Post by itzpapalotl on 2007-08-13
Well, gang. It has been a long and arduous summer, but by golly
We have a whole school who's vital systems are all open source. 
The brunt of my problem was replacing our current information system (Chancery Winschool) with an open source platform. (Focus-sis) It is done, it is working and it is running circles around our former services. My teachers are and staff are loving it. Doing their attendance right in class, inputting their grades from home. My old Win2k Server which was struggling as hard as it could just to provide NAT and LDAP to the system is now just singing along under Dapper Drake with OpenLDAP. Switching to Ubuntu was like buying a whole new structure. I will be beginning to take all the notes I have made over the summer, and compiling them to my site. This is very exciting. The only Non open source wares we have at this point are a couple of Windows boxes with some special software needed by the science department. 

I'm so happy I could scream!
Itz.

---

### Post by hsweet on 2007-09-24
I'm still at the stage of a single classroom and trying to interest the admins and tech folks so I'll not comment on school-wide stuff .  but

I think thin clients are well worth investigating.  You can set up a server on almost anything if you want to see how it works.  There is no nicer feeling than when I can remove or add a program for my whole lab in 3 minutes.  With a good server, your oldest computers will run like a brand_new_out_of_the_box.    You have to see it.  It really works.  It saves me orders of magnitude of time compared to setting up individual workstations, and I'm only worrying about 20.

As for high school level stuff.  Here are some I have found. (Of course most of the high school stuff is focused around writing making (ugh) powerpoints and the occasional spreadsheet...all handled by openoffice.

WxMaxima and Qalculate are a couple of great math programs.  Maxima is similar to mathamatica

Kalzium for chemistry

If your school teaches programming, there are all sorts of editors and languages, perl, php, python, ruby, and on and on.

Check out Ubuntustudio for music and video production, music scoring and so on.

You can set up web servers (apache), databases(mysql) name servers for web design classes.

Gimp, Inkscape, Xara, Blender are all excellent in art and technology graphics.

Scribus for desktop publishing.

Cad software need some work, though, and is the only reason I still am using windows in some of my classes,.

And oh, yeah, check out Clonezilla if you do need to image a couple of hundred clients (like ghost).

good luck

---

