---
title: "Profile-cleaner reduces browser profile size by cleaning/reindexing"
date: 2013-02-15
forum: Desktop Environments
---

### Post by graysky on 2013-02-15
Profile-cleaner reduces browser profile size by cleaning/reindexing their sqlite databases.

Direct benefits:
*Size reduction of profile databases (vacuum).
*Faster reads of profile databases (reindex).

Indirect benefits:
*Users of [profile-sync-daemon](http://ubuntuforums.org/showthread.php?t=2115685) will experience faster initial sync/unsync due profile size reduction.

Supported browsers: 
*Chromium
*Conkeror
*Firefox
*Google-chrome
*Heftig's Aurora
*Midori
*Thunderbird
*QupZilla

Sample output and results using an "uncleaned" firefox profile:
[[img]http://s19.postimage.org/cdb75hl2n/screen.jpg[/img]](http://postimage.org/image/cdb75hl2n/)

To add the PPA (personal package archive) to your Ubuntu (packages available for Lucid and newer) system, and to install psd:

```
$ sudo add-apt-repository ppa:graysky/utils
$ sudo apt-get update
$ sudo apt-get install profile-cleaner
```

If you can improve the code, plz send me a pull request.  Github: [https://github.com/graysky2/profile-cleaner](https://github.com/graysky2/profile-cleaner)

---

### Post by aleblanc on 2013-02-16
I get the following error when trying to install it in Ubuntu 12.04: 

```
The following packages have unmet dependencies.
 profile-cleaner : Depends: parallel but it is not installable
E: Unable to correct problems, you have held broken packages.
```


:(

---

### Post by graysky on 2013-02-16
> **aleblanc said:**
> I get the following error...

You need to enable [universe] which is where the Ubuntu devs keep parallel.  If you are unsure how to do this, see: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu)

---

### Post by ibjsb4 on 2013-02-16
I use FireFox with a large built in sqlite data base [(Zotero)]("http://www.zotero.org/") of about 700M. Is your package a good idea for this setup?

---

### Post by graysky on 2013-02-16
> **ibjsb4 said:**
> I use FireFox with a large built in sqlite data base [(Zotero)]("http://www.zotero.org/") of about 700M. Is your package a good idea for this setup?

My script is a gloried wrapper for `sqlite3 $db vacuum && sqlite3 $db reindex` both of which are standard commands and should work fine on any compatible database.

Best advice:

1) Backup your profile.
2) Run `pc f` which is shorthand for `profile-cleaner f`
The application will show you how many space (if any) was saved as a function of the vacuum and reindex commands.

Please report back.

---

### Post by aleblanc on 2013-02-16
I already had universe enabled, but parallel is only available in the 12.10 repositories.
However, I did manage to find an Ubuntu 12.04 package here:

[https://build.opensuse.org/package/show?package=parallel&project=home%3Atange]("https://build.opensuse.org/package/show?package=parallel&project=home%3Atange")

(scroll to the bottom of the page, there are also packages for many other distributions).

---

### Post by graysky on 2013-02-16
> **aleblanc said:**
> I already had universe enabled, but parallel is only available in the 12.10 repositories.

Why in the world would they not offer paralle to users of 12.04LTS? :roll:

---

### Post by aleblanc on 2013-02-16
No idea. 
Anyway, do you have any suggestions about what frequency to use in a cron script for profile-cleaner?

---

### Post by ibjsb4 on 2013-02-16
Dont understand why parallel is not offered for 12o4.  All dependencies are in place.  
So I downloaded the file and did a dpkg -i.  Seem to install just fine.

 [http://packages.ubuntu.com/quantal/parallel](http://packages.ubuntu.com/quantal/parallel)

---

### Post by graysky on 2013-02-16
@aleblanc - I runs it manually every now and then.  
@ibjsb - glad to here it's working for you.

---

### Post by ibjsb4 on 2013-02-16
profile-cleaner f
profile-cleaner v1.99

 Cleaning profile for firefox
 Cleaning addons.sqlite                        done  -0 Mbytes
 Cleaning signons.sqlite                       done  -0 Mbytes
 Cleaning content-prefs.sqlite                 done  -0 Mbytes
 Cleaning places.sqlite                        done  -0 Mbytes
 Cleaning permissions.sqlite                   done  -0 Mbytes
 Cleaning cookies.sqlite                       done  -0 Mbytes
 Cleaning webappsstore.sqlite                  done  -0 Mbytes
 Cleaning formhistory.sqlite                   done  -0 Mbytes
 Cleaning extensions.sqlite                    done  -0 Mbytes
 Cleaning index.sqlite                         done  -0 Mbytes
 Cleaning downloads.sqlite                     done  -0 Mbytes
 Cleaning zotero.sqlite.bak                    done  -3.10 Mbytes
 Cleaning zotero.sqlite.1.bak                  done  -3.10 Mbytes
 Cleaning zotero.sqlite                        done  -0 Mbytes
 Cleaning zotero.sqlite.73.bak                 done  -6.25 Mbytes

 Profile(s) for firefox reduced by 12.47 Mbytes.

Well that worked :)

---

### Post by graysky on 2013-02-17
@ibjsb4 - Glad you're finding it useful.

---

### Post by ibjsb4 on 2013-02-17
I was curious, so I asked

[https://answers.launchpad.net/ubuntu/+source/parallel/+question/222120](https://answers.launchpad.net/ubuntu/+source/parallel/+question/222120)

---

### Post by tille on 2013-02-19
edit:

sorry, just found out there is a unique option for the chromium profiles. Is the "google-chrome"-option for wine btw?

---

### Post by graysky on 2013-02-24
> **tille said:**
> edit:

sorry, just found out there is a unique option for the chromium profiles. Is the "google-chrome"-option for wine btw?

I don't use wine but I am assuming that the profile directory is somewhere under ~/.wine/.... so profile-cleaner doesn't know to look for it there.  Luckily for you, there is an option for you to use a non-standard path once you determine where it is:

```
% pc p /path/to/wine/chromium
```

---

### Post by Hodevah on 2013-02-24
```
user@user-desktop:~$ profile-cleaner f
profile-cleaner v2.01

 Cleaning profile for firefox
 Cleaning webappsstore.sqlite                  done  -0 Mbytes
 Cleaning urlclassifier3.sqlite                done  -0 Mbytes
 Cleaning signons.sqlite                       done  -0 Mbytes
 Cleaning places.sqlite                        done  -8.87 Mbytes
 Cleaning permissions.sqlite                   done  -0 Mbytes
 Cleaning httpsfinder.sqlite                   done  -0 Mbytes
 Cleaning formhistory.sqlite                   done  -0 Mbytes
 Cleaning firegestures.sqlite                  done  -0 Mbytes
 Cleaning extensions.sqlite                    done  -0 Mbytes
 Cleaning downloads.sqlite                     done  -0 Mbytes
 Cleaning cookies.sqlite                       done  -.37 Mbytes
 Cleaning content-prefs.sqlite                 done  -0 Mbytes
 Cleaning chromeappsstore.sqlite               done  -0 Mbytes
 Cleaning addons.sqlite                        done  -0 Mbytes
 Cleaning user595835.sqlite                    done  -0 Mbytes
 Cleaning index.sqlite                         done  -0 Mbytes
 Cleaning schema.sqlite                        done  -0 Mbytes
 Cleaning mappings.sqlite                      done  -.02 Mbytes
 Cleaning identity_1359822032765.sqlite        done  -.08 Mbytes
 Cleaning identity_1359562468347.sqlite        done  -0 Mbytes
 Cleaning identity_1359173573177.sqlite        done  -0 Mbytes
 Cleaning identity.sqlite                      done  -.08 Mbytes

 Profile(s) for firefox reduced by 9.43 Mbytes.
```


Well that went well.

---

### Post by graysky on 2013-02-27
@H - Good, glad it worked out for you.

---

