---
title: "How to: Speed Up application start-up time with preload 6.0.3"
date: 2009-02-24
forum: General Help
---

### Post by samoul on 2009-02-24
Preload is an "adaptive readahead daemon" that runs in the background of your system, and observes what programs you use most often, caching them in order to speed up application load time. By using Preload, you can put unused RAM to good work, and improve the overall performance of your desktop system. You can expect a 25-35% decrease in start-up time for all application.

The version in the repository is 4.3, I strongly suggest using the 6.0.3 version:
[https://launchpad.net/%7Etpikalek/+archive/ppa/+files/preload_0.6.3-0_i386.deb](https://launchpad.net/%7Etpikalek/+archive/ppa/+files/preload_0.6.3-0_i386.deb)
[https://launchpad.net/%7Etpikalek/+archive/ppa/+files/preload_0.6.3-0_amd64.deb](https://launchpad.net/%7Etpikalek/+archive/ppa/+files/preload_0.6.3-0_amd64.deb)

1) Download and install (by double clicking on the file) the package that fit you system.
2) If you have less than 1Gig of RAM I suggest not changing the default settings. Other allowing preload more space will increase your system performance.
Edit you configuration file with the folowing command: ```
sudo gedit /etc/preload.conf
```
CHANGE the folowing values:
"memtotal = -10" BY: ```
memtotal = 0
```
AND "memcached = 0" BY: ```
memcached = 50
```

That's it! Reboot your system so the new parameters takes effect. It will take preload 1-2 days to figure out witch program to preload. I have measured an average 25-30% decrease in application start-up time (tested Firefox, Thunderbird, Nautilus, Songbird, OpenOffice Writer). Bigger application seem to take more advantage of preload. Firefox start-up time decreased by 35% and OpenOffice Writer decreased by more than 75%. Tests we made under a 2 year old laptop with 1gig of RAM.

If you love the idea I encourage you to promote it on Ubuntu Brainstorm: [http://brainstorm.ubuntu.com/idea/18225/](http://brainstorm.ubuntu.com/idea/18225/)

Thanks!

More information on preload here:
[http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)
[http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

---

