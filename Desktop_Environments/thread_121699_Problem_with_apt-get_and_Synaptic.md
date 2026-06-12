---
title: "Problem with apt-get and Synaptic"
date: 2006-01-25
forum: Desktop Environments
---

### Post by koira on 2006-01-25
Hi, I am a new Ubuntu user, and have been trying to get this working for weeks.
Read through this forum, tried out the various  methods, and still failed

This is the error message whenever i run apt-get update:

root@YcComputer:~# apt-get update
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy Release.gpg
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates Release
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy Release
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports Release
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/universe Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/main Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/restricted Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/universe Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/main Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/restricted Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/main Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/restricted Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/universe Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/multiverse Packages
  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-amd64/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-amd64/Packages.gz)  Could not connect to sg.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Reading package lists... Done
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I checked out /etc/resolv.conf and the DNS servers are resolved correctly (counter checked with windows' ipconfig)
search ntu.edu.sg
nameserver 155.69.5.225
nameserver 155.69.5.7

The environment variables for network proxy has alrdy been set too.

Read that the repository may be down sometimes, but can they be down for that long? If apt-get can work, it'll make my life much easier getting the apps I want. In fact, I ran into the same problem wif fedora core's yum last time, which is why i switched over to Ubuntu to try things out

It seemed too that, other then my own school (NTU's) website/ip addresses that return a ping, pinging any other external websites/ip address returns nothing.

---

### Post by kaamos on 2006-01-25
> It seemed too that, other then my own school (NTU's) website/ip addresses that return a ping, pinging any other external websites/ip address returns nothing.
How did you set the proxy?
```

export http_proxy=http://the_proxy_here:port_number/
sudo apt-get update
sudo apt-get install <something>

```
Any luck?

---

### Post by koira on 2006-01-26
export http_proxy=http://the_proxy_here:port_number/

Ah, that works, or at least it apt-get seems to be updating itself alrdy

Previous to this, i set the proxy tru System->Preference->Network proxy menu. Strange that it didnt work

Thkz alot!

---

### Post by koira on 2006-01-26
Hmm.. wat does apt-get update do?
The update complete successfully, taking ard 15mins downloading stuffs from the various repos

After that, the update available icon flashed, prompting me to update. Hitting it gives this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.7-5ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.7-5ubuntu1.2_all.deb)
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.7-5ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.7-5ubuntu1.2_amd64.deb)
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
...

Running Synaptic or apt-get install <something> returns largely the same errors of being unable to fetch

---

### Post by kaamos on 2006-01-26
exporting the proxy like that is temporary. so you have to do that every time you open a terminal. Or add the line to /home/username/.bashrc and /home/username/.bash_profile

Synaptic has it's own proxy config. In synaptic choose settings->preferences->network and insert the proxy. Don't know what the update manager uses..

---

### Post by public_void on 2006-01-26
I'm behind a proxy as well, you have to edit the file /etc/apt/apt.conf, and add your proxy settings in there. Heres how in the terminal

cd /etc/apt/ (Changes the directory to /etc/apt/)
cp /etc/apt/apt.conf /etc/apt/apt.conf_backup (Copies the file apt.conf to the same directory be renames it apt.conf_backup. This is incase you make a mistake, you don't have to do that command)
sudo gedit apt.conf (Opens apt.conf in a text editor and allows you to edit it)
Add the lines

```
ACQUIRE { 
http::proxy "http://[UserName]:[Password]@[ProxyAddress]:[Port]/" 
}
```

If your proxy does not requires authentication then leave "[UserName]:[Password]@" out.

Save the file and exit the terminal.
Try sudo apt-get update. It should be able to connect to the respo servers and update.

---

### Post by koira on 2006-01-26
Nailed it. Phew, it finally worked, abeit the download is kinda slow, but hey! Its working, that's all that matters

Thkz all for helping me along with my baby steps along the path of ubuntu =)

---

