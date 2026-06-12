---
title: "What ports does apt-get/synaptic use?"
date: 2009-03-02
forum: General Help
---

### Post by civillian on 2009-03-02
I am using an ubuntu computer over my university's network, however, it seems that the ports that apt-get/synaptic use are closed. I can request that they be opened, but I cannot do that unless I know what ports that synaptic uses.
[edit]also, what protocol does apt/synaptic use? tcp or UDP? I need to know what protocol it will use, as well as the port(s) it uses to register a 'firewall hole'[/edit]

The particular problem I face is that I want to update my eeepc (running eeexubuntu 7.10) to 8.04 and then fix it all using the howto [here](http://wiki.eeeuser.com/ubuntu:eeexubuntu:upgrading_to_8.04)

I attepted to do 
```
sudo apt-get update
```

but it failed with this output

```
john@civint-eee701:~$ sudo apt-get update
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/universe Translation-en_GB   
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://archive.canonical.com gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/main Translation-en_GB           
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://archive.canonical.com gutsy/partner Translation-en_GB               
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_GB     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_GB     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://archive.ubuntu.com gutsy Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy/main Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy/universe Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy/restricted Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy/multiverse Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates/universe Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates/main Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates/restricted Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I presume this was due to the lack of support for the 7.10 repos and/or the denial of access to the internet of apt/aptitude/synaptic?

In anycase, the main question is 
1:what ports does synaptic/aptitude use to access the internet
and
2:is this actually what I need to update my ubuntu 7.10 to 8.04 (although I get similar errors on my 8.10 pc at uni too) or do I need to download/buy the entire package repos on CD? :P

Thanks for the help
Civint.

---

### Post by civillian on 2009-03-03
I found out I just had to direct it through the same proxy my browser was using...silly me :S

---

