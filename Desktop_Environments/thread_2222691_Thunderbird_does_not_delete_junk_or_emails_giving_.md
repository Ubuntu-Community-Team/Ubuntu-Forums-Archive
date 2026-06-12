---
title: "Thunderbird does not delete junk or emails giving error messages."
date: 2014-05-07
forum: Desktop Environments
---

### Post by TWFJR on 2014-05-07
Thunderbird must be corrupted: Error messages:

! Could not read chrome manifest 'file:///usr/lib/thunderbird/extensions/%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D/chrome.manifest'.

! While creating services from category 'profile-after-change', could not create service for entry 'Disk Space Watcher Service', contract ID '@mozilla.org/toolkit/disk-space-watcher;1'

! Use getPreventDefault() is depricated. Use defaultPreventedk [https://www.mozilla.org/thunderbird/js/jquery/jquery-1.5.1.min.js](https://www.mozilla.org/thunderbird/js/jquery/jquery-1.5.1.min.js)

Selector expected. Ruleset ignored due to bad selector.
about:blank
! . . .Class span,.ExternalClass font,.ExternalClass td,.ExternalClass div{line-height:100%}p{margin:1em 0};
--------------------------------------^


Unexpected end of file while searching for closing} of invalid rule set.
About:blank
!
---------^

Selector expected. Ruleset ignored due to bad selector.
about:blank
!
. . .Class span,.ExternalClass font,.ExternalClass td,.ExternalClass div{line-height:100%}p(margin:1em 0};
-------------------------------------^

Unexpected end of file while searching for closing}of invalid rule set.
about:blank
!
---------^

I've tried removing Thunderbird and reinstalling it but this problem persists.

---

### Post by pfeiffep on 2014-05-08
If you have an message backup you might consider purge (if you use synaptic the option is mark for complete removal) from man pages ... "purge is identical to remove except that packages are removed and purged           (any configuration files are deleted too)."

---

### Post by TWFJR on 2014-05-08
> **pfeiffep said:**
> If you have an message backup you might consider purge (if you use synaptic the option is mark for complete removal) from man pages ... "purge is identical to remove except that packages are removed and purged           (any configuration files are deleted too)."

I have used synaptic but I cannot find synaptic on the computer. It is installed. A search does not present synaptic package manager.

---

### Post by pfeiffep on 2014-05-09
I believe apt-get will purge also ... purge           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).
command ```
sudo apt-get purge thundebird
```

---

### Post by TWFJR on 2014-05-10
> **pfeiffep said:**
> I believe apt-get will purge also ... purge           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).
command ```
sudo apt-get purge thundebird
```

It has become evident that Ubuntu has made it very difficult to find hidden files. For instance, .Thunderbird. I cannot find Synaptic nor Thunderbird and so purging Thunderbird not an option without a mini-course to understand where such files and apps are kept.

---

### Post by TWFJR on 2014-05-10
> **TWFJR said:**
> It has become evident that Ubuntu has made it very difficult to find hidden files. For instance, .Thunderbird. I cannot find Synaptic nor Thunderbird and so purging Thunderbird not an option without a mini-course to understand where such files and apps are kept.

Copied/pasted purge command but thunderbird was mispelled so corrected and tried again. Seemed to have removed Thunderbird until I reloaded it and the same problem exists. Unable to delete email.

---

### Post by pfeiffep on 2014-05-10
Try this ...
```
whereis synaptic
synaptic: /usr/sbin/synaptic /usr/share/synaptic /usr/share/man/man8/synaptic.8.gz
```

---

### Post by TWFJR on 2014-05-11
Hi Pete, Thanks for your assistance; still no resolution..
tom@toms-desktop:~$  /usr/sbin/synaptic /usr/share/synaptic /usr/share/man/man8/synaptic.8.gz
bash: /usr/sbin/synaptic: No such file or directory

I'm beginning to think that it is not Thunderbird that is corrupted but 14.04.

---

### Post by pfeiffep on 2014-05-11
Did you type "whereis synaptic"  no quotes

---

### Post by ajgreeny on 2014-05-11
What error if any do you get from command ```
synaptic pkexec
```

---

### Post by TWFJR on 2014-05-12
I've got synaptic installed but cannot find purge instead I've found marked for complete removal. This does not solve the problem.

---

### Post by TWFJR on 2014-05-12
Every new install brings up a configured account. Nothing is purging Thunderbird nor does Synaptic fix Thunderbird as a broken package.

---

### Post by oldos2er on 2014-05-12
*apt-get purge <package>* and Synaptic's 'Complete Removal' will not remove any configuration files in your home folder, you will need to do that manually in your favorite file manager or in a terminal. The files are located at ~/.thunderbird/xxxxxxxx.default/ where "xxxxxxxx" is a random alphanumeric string.

All your mail and customizations will be deleted, so if you don't want that to happen move the entire xxxxxxxx.default folder somewhere else.

---

### Post by electrohandyman501 on 2014-05-12
I've also experienced thunderbird delete e-mail issues with a Yahoo mail account. I'd say that it started about 6mo ago or so. Sometimes it works, sometimes not.

---

### Post by TWFJR on 2014-05-18
Thunderbird lists this as local directory:  /home/tom/.thunderbird/mtjiadeg.default/Mail/Local Folders. .thunderbird  dirctory lists mtjiadeg.default and, in grey, unaccessible, profiles.ini. but no alphanumeric string. The only way I could see this was through browse in Thunderbird.

---

### Post by ajgreeny on 2014-05-28
If you are unable to look at the contents of the current profiles.ini file you possibly need to make yourself a new **profiles.ini** file in the .thunderbird folder with the following content

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=mtjiadeg.default

```

---

### Post by TWFJR on 2014-06-04
Moving through instructions I am finding that my problem still exists; unable to delete emails. "profiles.ini" exists and consists of the content you listed. Deleting, removing, purging Thunderbird and reinstalling produces the same, cannot delete email.

---

### Post by TWFJR on 2014-06-28
I've got this "Alert:" "Unable to locate mail spool file." Maybe someone can assist me in making this spool file and putting it where it belongs.

---

### Post by bapoumba on 2014-06-28
> **TWFJR said:**
> I've got this "Alert:" "Unable to locate mail spool file." Maybe someone can assist me in making this spool file and putting it where it belongs.
Is this with a gmail account ?

---

### Post by TWFJR on 2014-07-02
No, local IP email.

---

### Post by bapoumba on 2014-07-02
[https://bugzilla.mozilla.org/show_bug.cgi?id=911082](https://bugzilla.mozilla.org/show_bug.cgi?id=911082)
OK, never used or heard of a movemail account, would it apply to you ?

---

### Post by TWFJR on 2014-07-03
No fix offered and the case is closed.

---

