---
title: "Potential School Wide Linux Implementation"
date: 2009-04-05
forum: General Help
---

### Post by w8tah on 2009-04-05
Hello Folks:

I am the One Man IT shop for Medina Christian Academy, and am facing a potential situation that i am trying to avert in the future.  I am currently a largely Windows XP (fully patched and updated) network built on a Windows Server 2003 Active Directory domain.  I have some samba servers for file servers and an APACHE web development server.  We have ~150 desktops spread between the classrooms, offices and computer lab. The computers are mostly roughly 5 year old Pentium 4 gateways mostly have 40 gb hdd, onboard sound and video cards and between 512 and 1024 mb memory

I am seeing a problem in that XP support ends here in the next few days / weeks.  Our hardware will NOT support Windows Vista , and some of the reviews that I am reading are beginning to indicate that we will not be able to support Windows 7 (even if we can afford the licenses).

I spoke with our Executive Director today and he indicated a willingness to at least consider moving the entire school to linux as a potential solution.

We need to be able to do the following things...

- most of our computer classes use Microsoft Office -- thats covered with Open Office, so no problem there, the same for our teachers using office and the folks in the front office.

- each classroom is equipped with a SmartBoard interactive white board, -- SmartTech has linux software and drivers for them, so it may be a little bit of work but should be workable.

-- Printing -- we have a number of printers across the network -- couple of which are all in one type units by keyocera - and all stations/users need to be able to print -- so that means samba print server -- again -- probably take some development work but i am pretty sure it can be done.

-- domain (or whatever its called in linux) -- users need to be able to sign in on any computer, and have their files accessable similar to what happens when a user logs into a windows domain.  

-- Our School management software / gradebook -- not available in linux, but im wondering about using crossover office / wine or possibly VMWARE -- i'll need input on that -- its a client server app sort of the gradebook writes out text files that are imported into the main application which is based on microsoft access databases with a custom written interface -- might have to run a Virtual windows 2003 server to run the server portion of it -- and like wine or something for the users to access it -- i dont know

-- backup -- we have a quantum loader, so one way or another we'll need to be able to back stuff up

-- file servers -- ive got a couple linux file servers now -- but they are running samba i dont know how to share stuff via linux

im sure there are things that i have forgotten so if anyone has ideas / suggestions please chime in.

I am tentatively planning to use kubuntu, for the desktop environmen, and this project (if it goes) at least for now would be deployed summer of 2010 for use beginning in the fall of 2010

ANY and all input is welcome

Thanks

Tim Holmes
IT Director 
Medina Christian Academy

---

### Post by 3Miro on 2009-04-05
The younger people are, the easier it is to take on a new system (generalization, but usually holds). The biggest problem, I believe, is that the staff would complain for their icons being different. Prepare for that.

- Printing - Sharing a printer between Linux boxes is as easy as marking couple of check-boxes, I have done it at home. If you wish to let windows machines print as well, you will need samba or something of the sort (cannot help, I have never done it)

- The domain thing: I have seen it done many times and I believe it is easier to set up then windows. Now easier means easier for someone with no experience, if you are used to the windows setting, prepare for something different. I have never done it, I just know it is very doable.

- the main problems for the grade-book will be the Microsoft element. You can do Virtual Box (free) or VM ware I suppose (I have never done servers under those), however, crossover or wine wouldn't run as well (I don't think wine supports servers). My suggestion is to look around for an alternative to the MS program. Open office has its own database (free) and I don't know how complicated the program for grades is to code, you probably can do it, just may be too much work. Look at Eubuntu, they might have something of the sort.

- Linux runs on plenty of servers and administrative tasks such as backup are well supported. I expect no problems with the backup (just have to read on how to do it).

- I am sharing files between my Linux boxes via Samba, however, I don't like it. Samba runs using windows protocols and that is not very good. The Linux/Unix way to share files is NFS and I think it would work better: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

- the default Kubuntu looks closer to Windows, so it is a good choice. Make sure you use 9.04 or later and get KDE 4.2, 4.1 and earlier do not run very well (buggy). ( Actually for 2010, use 10.04 when it comes out )

Other notes:
- I am a mathematician and I need software to type my math formulas. I use LaTeX, however, I have colleagues that are using MS Office. Formulas form Ms Office format do not always display correctly under Open Office, especially if the Mac version has been used. If you have math teachers that use MS Office to type formulas, they may have to convert all of their old work to .pdf to read it under Linux. (Open Office has its own math plug-in that they can use for new documents)

One idea that I can give is to first try to convert only part of the system to Linux so you can test all the problems that might come up. At the same time you will still have the old system up and running so if there is a problem everyone can still get their work done.

---

### Post by Yashiro on 2009-04-05
I don't see a huge need to update your clients even when the so called support period expires.
Servers and your external facing equipment, sure, but the client machines?

If you're used to using AD and Group Policy the switch to managing Linux desktops is painful.
You could and should try to convert a sub section of client machines to Linux and see how that goes for you. No amount of internet testimonial will help when you actuallly come down to doing it.

---

### Post by jmszr on 2009-04-05
w8tah,
       For the School management software/Gradebook you should consider [http://moodle.org/](http://moodle.org/). 
Moodle is provided freely as Open Source software (under the GNU Public License).
 Example: [http://docs.moodle.org/en/Grades](http://docs.moodle.org/en/Grades) .
Here is the URL for installation in Ubuntu (I'm assuming Kubuntu would be about,if not totally, the same): [http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu](http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu). I just now registered on their website so that I could see what they had. I think it might be what you're looking for. Or part of it may be part of what you are looking for.

---

### Post by -kg- on 2009-04-05
Actually, according to the [Microsoft Website]("http://support.microsoft.com/lifecycle/?LN=en-gb&C2=1173") it is Mainstream Support that is being retired in a few days.  Extended support will be continued until 2014, including udates.  From an [article on InformationWeek:]("http://www.informationweek.com/news/windows/operatingsystems/showArticle.jhtml?articleID=208800494")

> In an unprecedented move, Microsoft (NSDQ: MSFT) has committed to providing support services for its soon to be retired Windows XP through 2014 -- a full 13 years after the operating system was originally released.

In a letter sent to customers this week, Microsoft senior VP Bill Veghte said the software maker will provide security patches "and other critical updates" for Windows XP until April, 2014...

...Microsoft may have little choice but to support Windows XP for an extended period, given that the majority of its large business customers have not upgraded their personal computers and laptops to the newer, Windows Vista operating system.

I don't mean to discourage your switch to Linux.  I think it is a very good idea to introduce young students to alternative OSes every bit as much as it is a good idea to introduce them to new ways of thinking and accomplishing things.  You never know...you may find yourself learning more from them than you teach them. ;)

I think Yashiro's idea of loading Linux (Ubuntu is probably a good choice) on a select subsection of machines is an excellent one.  That would allow you to learn on a few machines while maintaining the others with Windows.  If the worst happened, you could at least load XP back on those machines, and if the experiments were successful, convert the rest.

---

