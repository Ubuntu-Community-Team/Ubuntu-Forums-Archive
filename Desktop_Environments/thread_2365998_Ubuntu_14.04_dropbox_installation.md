---
title: "Ubuntu 14.04 dropbox installation"
date: 2017-07-13
forum: Desktop Environments
---

### Post by mrityunjay23 on 2017-07-13
I am new in dropbox installation on ubuntu. I am working behind proxy. The command ```
sudo apt-get install <some software>
``` works properly on my ubuntu 14.04 installed pc. I have installed dropbox through software center. It has not shown any error.  Surely it has installed successfully. When I click on dropbox icon it open one dialog box titled  "authentication is needed to run '/usr/bin/dropbox' as the super user and it ask super user password. After giving super user password I click on authenticate. My drop box does not start. When I type  following command on terminal ```
dropbox start -i
```  Then it gives following error. 

```
dropbox start -i
Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 1436, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1420, in main
    globaloptionparser.parse_args(argv[0:i])
  File "/usr/lib/python2.7/optparse.py", line 1400, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.7/optparse.py", line 1440, in _process_args
    self._process_long_opt(rargs, values)
  File "/usr/lib/python2.7/optparse.py", line 1515, in _process_long_opt
    option.process(opt, value, values, self)
  File "/usr/lib/python2.7/optparse.py", line 789, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.7/optparse.py", line 809, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "/usr/bin/dropbox", line 1408, in set_http_proxy
    urllib._urlopener = DropboxURLopener()
NameError: global name 'DropboxURLopener' is not defined
The installation of Dropbox failed.

```
When I type ```
sudo apt-get install nautilus-dropbox
``` on terminal it gives 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
nautilus-dropbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 179 not upgraded.
```

When I see software center it shows dropbox installed mean to say it shown Remove button.
In order to set proxy I use this below site
[https://www.dropbox.com/help/desktop-web/connecting-through-proxy](https://www.dropbox.com/help/desktop-web/connecting-through-proxy)
For setting proxy, when I right click dropbox icon it does not show Preference.
How to successfully install drop box in my system. May any body guide me.

---

### Post by thatsmyboy on 2017-07-13
Do you think the proxy or the installation is the sticking point? looks like there was a problem with the install to me.

---

