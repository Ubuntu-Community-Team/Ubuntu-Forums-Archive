---
title: "apt-get update: Sources.bz2  Hash Sum mismatch, aptitude update: no errors"
date: 2009-01-17
forum: General Help
---

### Post by Aidin Sabetian on 2009-01-17
After installing VirtualBox OSE when I run "sudo apt-get update" it returns the following error:
```
W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I uninstalled VirtualBox OSE and that didn't work, I reinstalled VirtualBox OSE but that didn't work either.
I have also tried "sudo apt-get update -o Acquire::http::No-Cache=True" and "sudo apt-get update -o Acquire::BrokenProxy=true" and received the same error.
I've also tried switching to the main server and to loads of different servers around the globe to no avail.

The strange thing is that "sudo aptitude update" completes without an error!

Operating system: Ubuntu 8.10 (Intrepid Ibex)
Machine: Compaq Presario 2500 32 bit laptop

1. How do I fix this problem?
2. What's the difference between apt-get and aptitude?
3. Does "sudo aptitude update" do the same job as "sudo apt-get update"?



Thanks for your consideration.
-- Aidin Sabetian


The contents of /etc/apt/sources.list:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ir.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ir.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ir.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ir.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ir.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ir.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ir.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ir.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ir.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ir.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by Aidin Sabetian on 2009-01-17
I again switched to the main server, now I get a different error when running "sudo apt-get update" and "sudo aptitude update":

```
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

Notice that "sudo aptitude update" which used to run without any errors now returns the same error as "sudo apt-get update".

I went to System > Administration > Software Sources > Authentication tab, then deleted every key, and restored the default keys and got the same error again.

---

### Post by Aidin Sabetian on 2009-01-17
I resolved the problem, here are the details:

The main server is overloaded and too busy serving probably thousands of users worldwide. Hence the error.

In System > Administration > Software Sources > Download from, I switched to an Italian mirror ([http://giano.com.dist.unige.it/ubuntu](http://giano.com.dist.unige.it/ubuntu)) and ran "sudo apt-get update", the problem went away!

---

### Post by Aidin Sabetian on 2009-01-22
The problem arose again after installing the adobe flash plugin.

"sudo apt-get update" using the mirror "http://giano.com.dist.unige.it/ubuntu" returns:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/intrepid-updates/Release  



W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/intrepid-security/Release  



W: Some index files failed to download, they have been ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems
```

"sudo aptitude update" using the mirror "http://giano.com.dist.unige.it/ubuntu" returns:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: You may want to run apt-get update to correct these problems
```


"sudo apt-get update" using the main server returns:
```
W: GPG error: http://archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2  Hash Sum mismatch



W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch



E: Some index files failed to download, they have been ignored, or old ones used instead.
```

"sudo aptitude update" using the main server returns:
```
W: GPG error: http://archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: You may want to run apt-get update to correct these problems
```
---
the output of "sudo apt-get update" using the mirror "http://giano.com.dist.unige.it/ubuntu":
```
0% [Working]
            
Hit http://archive.canonical.com intrepid Release.gpg


            
5% [Connecting to giano.com.dist.unige.it (130.251.19.2)]
                                                         
Hit http://giano.com.dist.unige.it intrepid Release.gpg


                                                         
10% [Waiting for headers]
                         
10% [Waiting for headers] [Waiting for headers]
                                               
Ign http://giano.com.dist.unige.it intrepid/main Translation-en_US


                                               
15% [Waiting for headers]
                         
15% [Waiting for headers] [Waiting for headers]
                                               
Ign http://giano.com.dist.unige.it intrepid/restricted Translation-en_US


                                               
20% [Waiting for headers]
                         
Ign http://archive.canonical.com intrepid/partner Translation-en_US


                         
25% [Connecting to giano.com.dist.unige.it (130.251.19.2)]
                                                          
Hit http://archive.canonical.com intrepid Release


                                                          
25% [Waiting for headers]
                         
25% [Release gpgv 7007] [Waiting for headers]
                                             
27% [Waiting for headers]
                         
Hit http://archive.canonical.com intrepid/partner Packages


31% [Waiting for headers]
                         
Hit http://archive.canonical.com intrepid/partner Sources


36% [Waiting for headers]
                         
Ign http://giano.com.dist.unige.it intrepid/universe Translation-en_US


                         
40% [Working]
             
40% [Waiting for headers]
                         
Ign http://giano.com.dist.unige.it intrepid/multiverse Translation-en_US


                         
45% [Working]
             
Get:1 http://giano.com.dist.unige.it intrepid-updates Release.gpg [189B]


             
4% [1 Release.gpg 0/189B 0%]
                            
94% [Working]
             
94% [Waiting for headers]
                         
Ign http://giano.com.dist.unige.it intrepid-updates/main Translation-en_US


                         
95% [Working]
             
95% [Connecting to giano.com.dist.unige.it (130.251.19.2)]
                                                          
95% [Waiting for headers]
                         
Ign http://giano.com.dist.unige.it intrepid-updates/restricted Translation-en_US


                         
95% [Connecting to giano.com.dist.unige.it (130.251.19.2)]
                                                          
95% [Waiting for headers]
                         
Ign http://giano.com.dist.unige.it intrepid-updates/universe Translation-en_US


                         
96% [Working]
             
96% [Waiting for headers]                                              30B/s 0s
                                                                               
Ign http://giano.com.dist.unige.it intrepid-updates/multiverse Translation-en_US


96% [Working]                                                          30B/s 0s
                                                                               
Get:2 http://giano.com.dist.unige.it intrepid-security Release.gpg [189B]


51% [2 Release.gpg 0/189B 0%]                                          30B/s 6s
98% [Working]                                                          30B/s 0s
98% [Waiting for headers]                                              30B/s 0s
                                                                               
Ign http://giano.com.dist.unige.it intrepid-security/main Translation-en_US


98% [Working]                                                          30B/s 0s
98% [Waiting for headers]                                              30B/s 0s
                                                                               
Ign http://giano.com.dist.unige.it intrepid-security/restricted Translation-en_US


98% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
98% [Waiting for headers]                                              30B/s 0s
98% [Waiting for headers]                                              30B/s 0s
                                                                               
Ign http://giano.com.dist.unige.it intrepid-security/universe Translation-en_US


99% [Working]                                                          30B/s 0s
99% [Waiting for headers]                                              30B/s 0s
                                                                               
Ign http://giano.com.dist.unige.it intrepid-security/multiverse Translation-en_US


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid Release


99% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
99% [Release gpgv 65861] [Connecting to giano.com.dist.unige.it (130.251.19.2)]
97% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
                                                                               
Get:3 http://giano.com.dist.unige.it intrepid-updates Release [51.2kB]


99% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
99% [3 Release gpgv 51208] [Connecting to giano.com.dist.unige.it (130.251.19.2
                                                                               
Err http://giano.com.dist.unige.it intrepid-updates Release

  


99% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid-security Release


99% [Working]                                                          30B/s 0s
99% [Release gpgv 44004]                                               30B/s 0s
                                                                               
Err http://giano.com.dist.unige.it intrepid-security Release

  


99% [Connecting to giano.com.dist.unige.it (130.251.19.2)]             30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/main Sources


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/restricted Sources


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/main Packages


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/restricted Packages


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/multiverse Sources


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/universe Sources


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/universe Packages


99% [Working]                                                          30B/s 0s
                                                                               
Hit http://giano.com.dist.unige.it intrepid/multiverse Packages


99% [Working]                                                          30B/s 0s
                                                                               
Fetched 379B in 10s (35B/s)


Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://giano.com.dist.unige.it intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/intrepid-updates/Release  



W: Failed to fetch http://giano.com.dist.unige.it/ubuntu/dists/intrepid-security/Release  



W: Some index files failed to download, they have been ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems
```

---

### Post by Aidin Sabetian on 2009-01-22
the output of "sudo apt-get update" using the main server":
```
0% [Working]
            
0% [Connecting to archive.ubuntu.com] [Connecting to archive.canonical.com]
                                                                           
0% [Connecting to archive.ubuntu.com (91.189.88.31)] [Connecting to archive.can
                                                                               
Hit http://archive.ubuntu.com intrepid Release.gpg


                                                                               
5% [Connecting to archive.ubuntu.com (91.189.88.31)] [Waiting for headers]
                                                                          
Hit http://archive.canonical.com intrepid Release.gpg


                                                                          
10% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
10% [Waiting for headers] [Waiting for headers]
                                               
Ign http://archive.canonical.com intrepid/partner Translation-en_US


                                               
15% [Waiting for headers]
                         
Hit http://archive.canonical.com intrepid Release


15% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid/main Translation-en_US


                         
20% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
20% [Release gpgv 7007] [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                                         
22% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
Hit http://archive.canonical.com intrepid/partner Packages


                                                     
27% [Waiting for headers]
                         
Hit http://archive.canonical.com intrepid/partner Sources


31% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US


                         
36% [Working]
             
36% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US


                         
40% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
40% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US


                         
45% [Working]
             
Hit http://archive.ubuntu.com intrepid-updates Release.gpg


47% [Working]
             
47% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US


                         
52% [Working]
             
52% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US


                         
56% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US


                                                     
60% [Working]
             
60% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US


                         
65% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
Hit http://archive.ubuntu.com intrepid-security Release.gpg


                                                     
66% [Working]
             
66% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US


                         
70% [Working]
             
70% [Waiting for headers]
70% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US


                         
75% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
75% [Waiting for headers]
75% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US


                         
79% [Working]
             
79% [Waiting for headers]
79% [Waiting for headers]
79% [Waiting for headers]
                         
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US


                         
83% [Working]
             
Hit http://archive.ubuntu.com intrepid Release


             
83% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
83% [Release gpgv 65861] [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                                          
65% [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                     
Get:1 http://archive.ubuntu.com intrepid-updates Release [51.2kB]


                                                     
0% [1 Release 0/51.2kB 0%]
                          
32% [1 Release 16847/51.2kB 32%]
                                
58% [1 Release 29707/51.2kB 58%]                                     4804B/s 4s
82% [1 Release 42367/51.2kB 82%]                                     4804B/s 1s
99% [Working]                                                        4804B/s 0s
99% [1 Release gpgv 51208]                                           4804B/s 0s
                                                                               
Ign http://archive.ubuntu.com intrepid-updates Release


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security Release


99% [Working]                                                        4804B/s 0s
99% [Release gpgv 44004]                                             4804B/s 0s
99% [Connecting to archive.ubuntu.com (91.189.88.31)]                4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/main Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/restricted Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/main Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/restricted Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/multiverse Sources


99% [Working]                                                        4804B/s 0s
99% [Waiting for headers]                                            4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/universe Sources


99% [Connecting to archive.ubuntu.com (91.189.88.31)]                4804B/s 0s
99% [Waiting for headers]                                            4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/universe Packages


99% [Connecting to archive.ubuntu.com (91.189.88.31)]                4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid/multiverse Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/main Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Get:2 http://archive.ubuntu.com intrepid-updates/restricted Packages [5770B]


89% [2 Packages 0/5770B 0%]                                          4804B/s 1s
99% [Working]                                                        4804B/s 0s
                                                                               
99% [2 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.31)]
                                                                          
99% [Connecting to archive.ubuntu.com (91.189.88.31)]                4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/main Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/universe Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/universe Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/main Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/restricted Packages


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/restricted Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/main Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources


99% [Working]                                                        4804B/s 0s
                                                                               
Get:3 http://archive.ubuntu.com intrepid-security/universe Sources [3589B]


99% [3 Sources 3588/3589B 99%]                                       4804B/s 0s
99% [Working]                                                        4804B/s 0s
99% [3 Sources bzip2 0]                                              4804B/s 0s
99% [Connecting to archive.ubuntu.com (91.189.88.31)]                4804B/s 0s
                                                                               
Get:4 http://archive.ubuntu.com intrepid-security/universe Packages [21.0kB]


99% [4 Packages 20951/21.0kB 99%]                                    5097B/s 0s
99% [Working]                                                        5097B/s 0s
99% [4 Packages bzip2 0]                                             5097B/s 0s
99% [Waiting for headers]                                            5097B/s 0s
                                                                               
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages


99% [Working]                                                        5097B/s 0s
                                                                               
Fetched 57.0kB in 18s (3031B/s)

W: GPG error: http://archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2  Hash Sum mismatch



W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch



E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Aidin Sabetian on 2009-01-22
I had this problem before but even after reinstalling Ubuntu I'm still getting the same errors.
I tried removing the authentication keys in "Software Sources" and restored the defaults to no avail

---

