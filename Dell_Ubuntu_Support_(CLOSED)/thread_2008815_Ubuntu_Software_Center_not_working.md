---
title: "Ubuntu Software Center not working"
date: 2012-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gww6 on 2012-06-23
Hey guys, I've been using Ubuntu for about a year now and I have never had this problem.  I just installed Ubuntu 12.04 LTS on my Dell Inspiron Duo 1090.  I was installing some basic software the I commonly use from the Software Center.  The last program that I tried to install was Dropbox.  For some reason, even after restarting, the software center is stuck "Searching Applying Changes".

I tried uninstalling and reinstalling via terminal.  No such luck.  Any advice guys?

---

### Post by nipunshakya on 2012-06-23
have u tried to run software-center from the terminal? do u get any error messages? open terminal and type:
```
software-center
```
 see if u get any errors about connections in the terminal...

---

### Post by gww6 on 2012-06-23
softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-23 11:18:39,865 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-23 11:18:41,219 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-06-23 11:18:43,772 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py:41: Warning: value "101.000000" of type `gdouble' is invalid or out of range for property `value' of type `gint'
  context.iteration()
2012-06-23 11:18:56,900 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-06-23 11:18:56,901 - softwarecenter.db.database - INFO - reopen() database
2012-06-23 11:18:56,902 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

---

### Post by nipunshakya on 2012-06-23
why don't u reinstall software center then...
in the terminal, type line by line the following codes:
```

sudo apt-get remove software-center
sudo apt-get install software-center
```

Try to see if that helps....

---

### Post by gww6 on 2012-06-23
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

It gave me that when I ran the remove code

---

### Post by nipunshakya on 2012-06-23
it means that either you are running software center currently or some update is being run on background(update manager) or maybe synaptic package manager.... Try finishing the background updates first and then run the command again...

---

### Post by gww6 on 2012-06-23
It's letting me run a partial upgrade.  I'm guessing that dropbox never finished installing for some reason.  Should I just run sudo apt-get remove dropbox

---

### Post by nipunshakya on 2012-06-23
give it a try.. worth it... i assume it might be the problem...

---

### Post by gww6 on 2012-06-23
It says:
E: Could not get lock /var/lib/dpkg/lock - open (ll: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I restarted the computer before doing this so I assumed that the Software Center wouldn't be running?  It seems like i'm stuck here.  I've never had this problem in Ubuntu before

---

### Post by nipunshakya on 2012-06-23
Try to see if there is any process running thats related to software-center. Open System Monitor, under the Processes tab, search for software-center. Kill the process, and then try to reinstall software center... this is the first time im seeing such problem with the distro

---

### Post by gww6 on 2012-06-23
I see the update notifier.  But that is the only thing I see that is even close.  I don't see the software center obviously until I open it.

---

### Post by gww6 on 2012-06-23
The only thing close to the software center is Update-notifier.  Nothing is running that looks like it could be from the software center.

---

### Post by nipunshakya on 2012-06-23
The update notifier is a separate thing. Hmm... Have u tried to run an update recently?  or does the update process fail too? is it just the software center's fault or is there a problem with synaptic package manager too? have u checked that?

---

### Post by gww6 on 2012-06-23
I just installed and updated last night.  I had to do a bunch of work to get the touch screen and multi-touch to work.  I had no issues when I quit working on it last night.  Right now, the update process will not work.  It says It can run a partial upgrade, but even that isn't working.  I figured I would come on here to see if someone much better at coding linux than me had any idea.

---

### Post by nipunshakya on 2012-06-23
try running an update too..
```
sudo apt-get update && sudo apt-get upgrade
```
See if update works too...

---

### Post by nipunshakya on 2012-06-23
> **gww6 said:**
> Right now, the update process will not work.  It says It can run a partial upgrade, but even that isn't working.

Partial upgrade? does partial upgrades exist? why dont u try to post the o/p of above update command?

---

### Post by gww6 on 2012-06-23
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sffvba[e0rt on 2012-06-23
To remove the lock just delete the file lock in the respective directories that are mentioned.

Problem here is as soon as you run Software Center the pending will still show... and even if you run apt-get update etc. it will simply try and continue to install Dropbox... This is the issue I am also currently having (and the list of threads about this is growing)...

I suspect we just need to find a way to delete the cache that states we are installing dropbox so we can use the tools normally but I am not sure what and how :/


404

---

### Post by gww6 on 2012-06-23
How do I do that?  I'm still relatively new to this.

---

### Post by nipunshakya on 2012-06-23
I guess its a bug that is being filed by others too... found something in the link below:
[http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99](http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99)

---

### Post by nipunshakya on 2012-06-23
u can try:
```

sudo dpkg-reconfigure dropbox
```
or you can try
```
sudo apt-get install -f
```

---

### Post by gww6 on 2012-06-23
Never mind, reinstalling Ubuntu now.  Thanks for the help guys

---

### Post by nipunshakya on 2012-06-23
please be specific and state which command was useful or not useful or what the outputs were.. i can only assume if u don't show the exact results.. so its good if u improve your posting skills... without details, none can help u right...

---

### Post by gww6 on 2012-06-23
The bug report you posted had the only known working fix.  I reinstalled the OS and will just leave Dropbox off of it until the program gets fixed.

---

### Post by nipunshakya on 2012-06-23
though not totally the solution to the problem, glad u got something around... Goodluck in future

---

### Post by akilas89 on 2013-05-30
I also have the same problem after updating Ubuntu to the newer version my software center is not responding. I tried opening it thru the terminal I get these prompt:
2013-05-30 12:19:41,852 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-30 12:19:41,858 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-05-30 12:19:42,631 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-30 12:19:42,638 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-05-30 12:19:42,638 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-05-30 12:19:42,736 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-05-30 12:19:42,738 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Malformed line 1 in source list /etc/apt/sources.list.d/google-chrome.list (dist parse)
2013-05-30 12:19:43,852 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 173, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 324, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 119, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 253, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 238, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

---

### Post by dtprint-olsztyn on 2013-09-01
Sorry for my English :)

When anybody have problem with Ubuntu Software Center.
1. restart Ubuntu
2. start terminal (ctrl+alt+t)
3. Try command:

mv ~/.cache/software-center{,.bak}

Last command renaming the software-center cache in your home directory.
Then try software center again.

Or try this:
1. restart Ubuntu
2. start terminal (ctrl+alt+t)
3. Try command

sudo apt-get remove software-center
sudo apt-get install software-center
mv ~/.cache/software-center{,.bak}

Then try software center again.
 Must be working :)

---

### Post by mscilley84 on 2013-09-11
confirmed dtprint-olsztyn....The first line worked the first time...Thank you. Just a newb question though.  What did that do?

---

### Post by kedar-anwardekar3 on 2014-03-28
software center is just a front end tool to apt 
you can go for synaptic package manager, Kpackage*, packagekit * if software center is not workin*g*

---

