---
title: "Encrypt only the home folder"
date: 2009-03-29
forum: Desktop Environments
---

### Post by qsdgfh5 on 2009-03-29
[Actually I wanted to comment on this thread ([http://ubuntuforums.org/showthread.php?t=238867&page=2](http://ubuntuforums.org/showthread.php?t=238867&page=2)) but I couldn't so opening another one]

I tried this guide [https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder) with my **Intrepid** but I assume it's outdated, even though it was updated this month.

I did the following:
```
sudo aptitude install libpam-encfs fuse

sudo modprobe fuse
echo "fuse" | sudo tee -a /etc/modules
```

All fine up till here offcourse

Then I should add the following to /etc/pam.d/common-auth:
```
auth sufficient pam_encfs.so
auth requisite pam_unix.so nullok_secure use_first_pass
auth optional pam_smbpass.so migrate use_first_pass 
```

There is no comment about those that are already there. I assume the following need to be commented out then?
```
#auth	[success=1 default=ignore]	pam_unix.so nullok_secure
#auth	requisite			pam_deny.so
#auth	required			pam_permit.so
```

"Configure the encfs PAM module" isn't written clear:
/ect/security/pam_encfs.conf is the configuration file for the pam_encfs.so **we just added to common-auth**. Change "allow_other" to "nonempty".
    * $ sudo gedit /etc/security/pam_encfs.conf 

There is no sign of common-auth or pam_encfs.so in my conf file so what should the content of pam_enfs.conf then actually be?

Mine is currently as follows:
```
encfs_default --idle=1
fuse_default allow_root,nonempty
-		/home/.enc	- 		-v			allow_other
```

I assume the following line is incorrect
    * $ sudo useradd testuser fuse 

and should be:
    * $ sudo adduser testuser fuse 

Does someone have a complete (and not an outdated one) tutorial for an encrypted home folder?

---

