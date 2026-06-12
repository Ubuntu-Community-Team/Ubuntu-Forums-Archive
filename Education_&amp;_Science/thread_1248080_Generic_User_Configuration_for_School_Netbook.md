---
title: "Generic User Configuration for School Netbook"
date: 2009-08-23
forum: Education &amp; Science
---

### Post by Nubnut on 2009-08-23
Hi All,
I'm in the process of configuring a base build Edubuntu 904 Netbook (eeepc 1005 HA) for use in a school.
When complete this base build will be cloned across 250 Netbooks and rolled out to Students and Teachers.
I've set up the default user during the initial build, and also I've set up a generic student account. This is the account I'm wondering about.
At Roll-Out each unit's Student Account will be renamed for the specific user it is rolled out to. This account can perform all functions except "Administer the System"
Once the Netbooks are rolled out to Students I'd like the updates to happen without user intervention, but I would also like for Students not to be able to administer their systems.
The plan is to use Clonezilla or equivalent on a central server to store this base build (and also previous laptop builds)

If I set Update Manager to check for updates every week, and check "Install security updates without confirmation", will this mean that updates happen automatically and students wont need to provide the root password?

Perhaps there is another way of achieving this, or a document somewhere detailing the best default user set-up for Netbooks which are rolled out in schools?

Any help or advice is greatly appreciated.

rgds

nubnut

---

### Post by PGScooter on 2009-08-24
I almost clicked the LTS (but did not). You should use one of the notebooks and do updates continuously. That way you can see if any of the updates break something. An alternative to your update setup would be to have a script that does it. I think something like this would do it:
```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

This sounds like a cool project! please post back with how things are going and where you run into problems.

---

### Post by bigbrovar on 2009-08-24
well i happen to be a sysad for a college and i had faced the same challanges you are facing now (although in my case its laptops and not netbooks) so let me share some of my experience with u

At first we decided not to give root privileges to the, hence they could not install applications or update the systems. the system was pre-configured to just work. i also created a new user account profile. which every account created on the system would use ( the configured account had special firefox links to our helpdesk and wiki etc)

at first we used the kitchen approach installing every edu software under the sun (we figured since the student wont be able to install apps we used just install everything under the sun for them and there would choose what is needed from there)

for a clone server we used [systemimager]("http://wiki.systemimager.org/index.php/Main_Page")  systemimager is an awesome tool it allows us to have a central image that his configured and then pushed out to the laptops, most of the updates we did on the laptops were pushed via systemimager.

issues we had with this approach
although the idea was to have the student laptops to be centrally administered, so as to reduce the chances of them breaking the system, and give us the admin less thing to worry about. in reality it was much trouble than is worth, we usually get lots of request the need to install this or that software, and the system imager model although works perfectly on our desktops (because there were fixed computers) it didnt work as planned on the laptops which wasnt fixed and u cana have a situ were a user switches off his laptop while systemimager is rsyncing and stuff.. also although hardy heron worked fine on the desktop. for the laptop i noticed that the recent version of ubuntu (9.04) had even better hardware support, better startup time, more updated edu software, and better support for hibernation and ****.

in light all this we changed out model and adopted another model which 

gave greater power to the laptop user, so users can install apps and updates themselves. We created a separate sub menu (under gnome panel) called aust (for African university of science and technology) there are a list of applications supported by the IT department. issues with any of this applications could be brought to the IT department for support and ****. However if the user installs an app himself he is own his own and we would not be able to support the app and if his system start acting up the best we can offer him is to re-image the system to default.

we had to switch out cloning server to [fog]("http://www.fogproject.org/") which is really damn good for the model we are using, we get to easy to install and setup.  we moved the laptop base to jaunty which works very well with no issues at all.  

so in the end we have a system were the student have greater have greater control over their system (but with the usual caveats) 
the advantage of this is the student can get to admin their system, install what they need, and we on the other hand give them a very light system which just the essential software needed to get them started. hence the system is not bloated.

for inventory we use [ocsinventory]("http://www.ocsinventory-ng.org/") so we have agent of the inventory system installed on all the laptops which allows them to report ot the image server hence we easily keep track of out laptops and ****.. 

well that is all i can see .. if u have any question or suggestions please u can always post them here or better still drop by our irc #aust @ freenode hope i was of help .. cheers

---

### Post by ugm6hr on 2009-08-24
I would agree that just letting everyone have sudo access to their own system will be easier in the long run.

Given they are students, you will have a handful just wipe your installed OS and start afresh anyway (that is what I would do).

Why not offer a standard OEM support model as default: if it doesn't work, it will be re-imaged as new.  That way, it takes 5 minutes to fix anything that the user breaks.  If you are feeling generous, you could offer to recover documents from home before doing this.  This is how most universities supply their work laptops (even with MS Windows), and it works well enough.

---

### Post by bigbrovar on 2009-08-24
> **ugm6hr said:**
> I would agree that just letting everyone have sudo access to their own system will be easier in the long run.

Given they are students, you will have a handful just wipe your installed OS and start afresh anyway (that is what I would do).

Why not offer a standard OEM support model as default: if it doesn't work, it will be re-imaged as new.  That way, it takes 5 minutes to fix anything that the user breaks.  If you are feeling generous, you could offer to recover documents from home before doing this.  This is how most universities supply their work laptops (even with MS Windows), and it works well enough.

yeah and we found that out the hardway,

also remember to password the bios make sure the only boot option available is boot from harddisk.. this would prevent people from booting from live cds or usb .. or installing another OS

---

### Post by Nubnut on 2009-08-24
Thanks for the advice guys, this is really helpful.
I should clarify our setup.
The "Connect School" is a secondary school, [http://www.staidanscs.com/]("http://www.staidanscs.com/") our students range from 12 to 17 yrs of age. It's for this reason I dont want them to administrate the system, at least not until they learn a little about using linux.
We use Moodle for our Virtual Learning Environment, [http://connect.learnonline.ie/]("http://connect.learnonline.ie/")
and use Google Docs for document managment. This means that reimaging problem units is possible since all user data should be stored remotely.

The way I've been managing Laptops(Windows XP builds) to date is to create a master build and keep this system updated. This updated build is used to re-image problem units using clonezilla.
All users are set up as limited users.

Ronan

---

### Post by bigbrovar on 2009-08-24
>  Nubnut  	
Re: Generic User Configuration for School Netbook
Thanks for the advice guys, this is really helpful.
I should clarify our setup.
The "Connect School" is a secondary school, [http://www.staidanscs.com/](http://www.staidanscs.com/) our students range from 12 to 17 yrs of age. It's for this reason I dont want them to administrate the system, at least not until they learn a little about using linux.
We use Moodle for our Virtual Learning Environment, [http://connect.learnonline.ie/](http://connect.learnonline.ie/)
and use Google Docs for document managment. This means that reimaging problem units is possible since all user data should be stored remotely.

The way I've been managing Laptops(Windows XP builds) to date is to create a master build and keep this system updated. This updated build is used to re-image problem units using clonezilla.
All users are set up as limited users.

Ronan 

hmm in that case you can always do that .. lock down the system since in your case you seem to have a list of what the students would need .. hence u can always configure the laptop to meet that needs .. 

FYI sudo is very flexible and u can configure it to give the students some limited powers or add them to things like the cups group so they would have powers to print for example .. also as suggested you can also use the oem tool to configure a system.. i tried it once and it would pretty good .. 

In my case every system has an admin user.. which i use in creating the default profile

---

### Post by lord_alan on 2009-08-24
This is a great project to share with the team at [Open Source Schools]("http://opensourceschools.org.uk/"), I'm sure the readership there (,yself included) would be extremely interested in how you get on.

I would tend to concur with the other contributors, maintaining centralised control with *no* sudo access for users will be quite hard to keep up I think.

Another idea could be to host your own repository and lock down things like an apt proxy so the students can only ultimately install what you want them to... That way you can control when updates are issued etc. At least running an apt cache will help to reduce the volume of updates that need to be pulled from the Ubuntu main repos and thereby keep your Internet access traffic lower.

Keep up the great work.

---

### Post by bigbrovar on 2009-08-24
> **lord_alan said:**
> This is a great project to share with the team at [Open Source Schools]("http://opensourceschools.org.uk/"), I'm sure the readership there (,yself included) would be extremely interested in how you get on.

I would tend to concur with the other contributors, maintaining centralised control with *no* sudo access for users will be quite hard to keep up I think.

Another idea could be to host your own repository and lock down things like an apt proxy so the students can only ultimately install what you want them to... That way you can control when updates are issued etc. At least running an apt cache will help to reduce the volume of updates that need to be pulled from the Ubuntu main repos and thereby keep your Internet access traffic lower.

Keep up the great work.

we use apt-cacher here and its been a bandwidth saver too .. all our computers here gets their updates from it .. we even had common ppa and 3rd party repos its a must of an env with lots of ubuntu computers

---

### Post by Nubnut on 2009-09-17
Hi Guys,
Turns out the suppliers are having a tough time figuring a cloning tool that handles linux. I've suggested Clonezilla and theyre testing this, any other ideas?
Ro

---

### Post by ugm6hr on 2009-09-18
PartImage?

---

