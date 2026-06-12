---
title: "Widget for To-Do Tasks on desktop?"
date: 2020-08-05
forum: Desktop Environments
---

### Post by razorrob on 2020-08-05
Hi

I'm new to linux and Ubuntu ... I've looked around but cant find anything as yet, are there any decent widgets for the desktop that are for to-do/tasks? In Windows I used apps such as Rainlender widget ... the is able a .deb file available for Ubuntu on Rainlender website, but when I try install it, I get an error message ... maybe I'm installing it wrong, I'm not sure ... in case anyone interested ... here's a link ...
[https://www.rainlendar.net/cms/index.php?option=com_rny_download&Itemid=30](https://www.rainlendar.net/cms/index.php?option=com_rny_download&Itemid=30)

But I'd really like to know if there are any decent tasks widgets out there that can be used.
I'm currently using KDE via Kubuntu, but it seems widgets work cross/flavors ... running latest Ubuntu v20.04

TIA

---

### Post by ActionParsnip on 2020-08-05
What is the message. Seems to just extract a set of pre-compiled files from the Rainlendar-Lite-2.15.4-amd64.tar.bz2 on the website.

If you run the rainlendar2 binary in the folder that extract from it, what are you shown? This isn't a deb so you may need to satisfy dependencies manually. I checked for a PPA on Launchpad and there isn't one (which is a shame).

Running the binary from the terminal may help as you can see the output(s) which can help diagnose issues.

---

### Post by TheFu on 2020-08-05
Linux isn't like Windows.  Don't go looking for software on the web and downloading packages, especially when you are really new.  Doing that is a good way to break your system, break APT dependencies, and end up with a system that cannot be patched.  The only answer will be to reinstall.  The problems usually take a few months before they show up.

So ... use whatever package manager front-end tool you like.  Software-Center, Synaptic, apt, apt-get, aptitude ... and search for packages with "to-do" or "task" in the description.

As for a widget, you can make one that launches it easily.  Just right click on the menubar, should be clear. If not, any of the "Ubuntu User Guides" or "Lubuntu User Guide" will have instructions.

**gnome-todo** and **etm-qt** are task managers.  
Or you could use almost any little notepad application - gnome-note (package **gnote** or knote) is handy for little stuff like this.  If you want more capable, use from anywhere, todo lists, there are many other options.

The key is to stay inside the package manager for all software installed with very, very, very few exceptions.  I've been in "dependency hell" before, but found that NOT using random downloads avoids that problem.
[B]Order of Installed software preference:
[/B][LIST=1]
[*]Canonical Repos
[*]Trusted 3rd party Repos
[*]Trusted PPAs
[*]Snaps, Flatpaks, AppImages (these are nearly self-contained, run-anywhere, packages, but have some great or terrible conditions of use) - snap-store, flatpak store.
[*].deb package files from Trusted sources - never random. Expect dependency faults in a few months.
[*]Source code installs - be certain to install to /usr/local/ as the PREFIX option. If you are a software developer, this may be 1st in your list, for the languages and projects that you work with or need as a dependency.
[/LIST]

Snaps, Flatpaks, AppImages provided directly by the project team could be higher in the order.  Those provided by untrusted 3rd parties shouldn't be considered, regardless of where they originate.

Back to todo stuff. I used todo.sh for about a year long ago, but quickly outgrew it.  Ended up using a spreadsheet with the GTD methodology.  I have a script that runs the program on each of my desktops that connects to the system where all my todo data is located and with the tool I like. 

It makes sense if you use the GTD method.  [https://lifehacker.com/productivity-101-a-primer-to-the-getting-things-done-1551880955](https://lifehacker.com/productivity-101-a-primer-to-the-getting-things-done-1551880955) is a quick-start explanation.  If you only have 25 items on a todo list, GTD is overkill.

The problem with these little tools is that they change every release just enough to drive me nuts. By using something else, I get control over when a change gets made, the data format, and the ability to import/export data.  Some day, I'll change from that .xls to an .ODS file or back to a text/csv file.  I've been using the same basic spreadsheet since around 2005. Really needed it 10 yrs earlier in my career.

Rainlender looks to be a calendar application.  Is that really what you seek?  There are lots of great calendar solutions for Linux that allow us to have 100% centralized calendars, available from anywhere in the world, from almost any client system we can imagine.

I've been using Thunderbird+lightning for that since before Thunderbird was made - back when it was Netscape Navigator and included News, Mail, Calendars, etc.  If you prefer a local file, something like "plan" can work. If an MTA is configured for the system, it will send reminders for upcoming events.  These days, I thought most people just used the calendar on their phones.  Having the same data centralized "somewhere" has been my goal for decades.  I know that calendaring data is all in my Zimbra system. Same for Address/Contacts.  Email is also in Zimbra.  From there, I can access all that data from a multitude of clients - phones, tablets, desktops, web-interfaces, whatever.  Zimbra has a crappy To-Do which I never liked.  Used gnote for 5-20 items - perhaps just for today.  

Nextcloud has a "Tasks/Todo" module ... and it hooks into Zimbra for mail, calendars, contacts ... meh.  The Task list is supposed to sync automatically, but it gets confused IME.

Of course, if you are stuck wanting Rainlender and have a valid .deb file for the current 20.04 Ubuntu release, then after downloading the file, use 
```
sudo apt install /full/path/to/Rainlender-version.deb
```
or
```
sudo apt install ./relative/path/to/Rainlender-version.deb
```
Apt, the program "apt", not to be confused with "APT" the general term for all package management front-ends, DBs, and dependency validators on Ubuntu, Mint, and Debian, systems, will install .deb files, then get the dependencies and install those, if possible.  Sometimes the dependencies cannot be resolved. That's a warning NOT to force the install.

Sorry if this was much more than you wanted, but the specific order for finding software to be installed is very important for people new to Ubuntu to understand.
Probably 99% of the software on my systems are from the Canonical repos.  I have less than 10 snaps/flatpaks/AppImage installed across all the systems here - about 25 systems.  There are a few python applications that the Canonical repos are 2-yrs behind on which need to be updated to keep functioning with the web-sites they do. Fortunately, the main one used (which we can't mention here) can update itself and whenever it stops working, a quick *name-of-app -U* handles that.  

We all have slightly different needs. Mine aren't the same as everyone else's.

---

### Post by rebecca58 on 2020-08-14
Very interesting. I learnt a lot from your post too.

---

