---
title: "NFS Permission Problems"
date: 2009-02-21
forum: General Help
---

### Post by Axanon on 2009-02-21
I am having trouble changing file permissions on an NFS network mounted drive. I have read some other threads about this but nothing seems to fit my situation. Perhaps somebody can point me in the right direction.

I should mention that I made a mistake when I reinstalled 8.10 by using a different username than before. I thought I could recover my old home folder by adding a user with the same name and changing the home folder to my old one. Anyways, this failed and there is no sense in harping on the past. I didn't realize the importance of the ID #'s. I do now though.

So, I have 2 accounts now. The primary one 'axanon', and the one I want to use 'sgallant' When I mount the drives to ~/whereiwant they appear to be owned by 'axanon'. what I am trying to do is change the ownership and group permissions to 'sgallant' but I can't do this with 'gksu nautilus' or through the command line with 'sudo chmod' or 'sudo chown'. I get errors telling me it can't be done.

Can somebody tell me how to do one of 2 things (in a safe way):
1.) change the UID/GID of 'sgallant' to 1000 and remove 'axanon'
or
2.) change the permissions of the share to allow 'sgallant' to have r/w access.

If any of this information helps:

PC-2//etc/exports is:
```

/home/sgallant/htdocs/ 192.168.2.10(rw,secure,sync)
/home/sgallant/utils/ 192.168.2.10(rw,secure,sync)

```

PC-1//etc/fstab is:
```

PC-2:/home/sgallant/htdocs /home/sgallant/htdocs nfs defaults 0 0
PC-2:/home/sgallant/utils /home/sgallant/utils nfs defaults 0 0

```

On PC-1, the UID/GID are:
axanon UID: 1000 GID: 1000
sgallant UID: 1001 GID: 1001
(if there is a way to list this from the command line or a conf file, help would be appreciated)

On PC-2, the UID/GID are:
sgallant UID: 1000 GID:1000

I'm still pretty new to linux, so if you need more information it would help to tell me how to give it to you. Thanks.

---

### Post by Jose Catre-Vandis on 2009-02-21
Try playing around with usermod which will allow you to change username and user ID. of particular interest might be the "-o" option which allows two UIDs that are the same?

Usage:

```
usermod -l login-name old-name
usermod -u UID username
```
```
man usermod
```

I remember having a similar problem once, but solved it by starting all over again!

Also, try moving your shares out of ~/home directories, and if your network is internal and secure you could always change file permissions on the server to 777? I have all my nfs homelan share files on 777 which allows everyone to access everything :)

---

### Post by Axanon on 2009-02-21
> **Jose Catre-Vandis said:**
> Try playing around with usermod which will allow you to change username and user ID. of particular interest might be the "-o" option which allows two UIDs that are the same?

Usage:

```
usermod -l login-name old-name
usermod -u UID username
```
```
man usermod
```

I have seen a few posts where messing around with this can cause some severe problems. I want to avoid that unless somebody can tell me exactly what I should do. I will give whatever information possible to achieve this!!

> **Jose Catre-Vandis said:**
> 
I remember having a similar problem once, but solved it by starting all over again!

This is not something I want to do all over again. There must be an easier way.

> **Jose Catre-Vandis said:**
> 
Also, try moving your shares out of ~/home directories, and if your network is internal and secure you could always change file permissions on the server to 777? I have all my nfs homelan share files on 777 which allows everyone to access everything :)
Please, correct me if I am wrong, but isn't (almost) everything outside my home folder only root accessible? I can only see a lot of hassle coming from this. I am looking for a solution a little more seamless and viable. Thank you for your input though.

**Edit:**
I did see one similar problem about somebody doing this on another type of machine (Usparc maybe?) and it involved changing a .map file. I do not know if this solution would work, but I could not find a similar .map file on either of my systems in /etc/nfs. (it doesn't exist). However I would like to know if there is there some config file somewhere that I can change access in? or does it always need to be 1000 -> 1000 or 1001 -> 1001 type of setup?

---

### Post by Jose Catre-Vandis on 2009-02-23
> **Axanon said:**
> 

Please, correct me if I am wrong, but isn't (almost) everything outside my home folder only root accessible? I can only see a lot of hassle coming from this. I am looking for a solution a little more seamless and viable. Thank you for your input though.



Not a problem if you chmod 777 all your files :)

The mapping idea sounds plausible, not tried it though.

I'll also have a play with usermod on my test system and report back

---

### Post by fragos on 2009-02-23
I'd try making the two users members of the same group.

---

### Post by Jose Catre-Vandis on 2009-02-24
Have had a play on my test system and was able to take out the username for the "primary home directory" and replae it with another one. 

I was able to do this through the GUI - Users and Groups, by creating a dummy Admin user, logging in as the dummy, then deleting users as necessary. I then added a user with the name I wanted, making sure that user was number 1000. Just doing this gives you errors on login, so you need to change permissions on the home folder:
```
sudo chown "preferred user" /home/primary home directory
sudo chgrp "preferred user" /home/primary home directory
sudo chmod -R 644 /home/preferred home directory
```

I could then access the nfs share without any permissions issues
 
Changing the name of the primary home directory is a different ball game - see [here]("http://ubuntuforums.org/showpost.php?p=4021450&postcount=2")

Then just get rid of the dummy user when you are done

If you can live with the home directory staying as the old name, simply
```
sudo usermod -l newname oldname
```
but make sure "newname" is not already on the system, so you might need to delete "newname" if it does already exist.

---

### Post by Jose Catre-Vandis on 2009-03-01
Re mapping, here is an exceprt from the man exports page:
>  User ID Mapping
       nfsd bases its access control to files on the server machine on the uid
       and gid provided in each NFS RPC request. The normal  behavior  a  user
       would expect is that she can access her files on the server just as she
       would on a normal file system. This requires that  the  same  uids  and
       gids  are used on the client and the server machine. This is not always
       true, nor is it always desirable.

       Very often, it is not desirable that the root user on a client  machine
       is also treated as root when accessing files on the NFS server. To this
       end, uid 0 is normally mapped to a different id: the  so-called  anony&#8208;
       mous or nobody uid. This mode of operation (called &#8216;root squashing&#8217;) is
       the default, and can be turned off with no_root_squash.

       By default, exportfs chooses a  uid  and  gid  of  65534  for  squashed
       access.  These values can also be overridden by the anonuid and anongid
       options.  Finally, you can map all user requests to the  anonymous  uid
       by specifying the all_squash option.

       Here&#8217;s the complete list of mapping options:

       root_squash
              Map  requests from uid/gid 0 to the anonymous uid/gid. Note that
              this does not apply to any other uids  or  gids  that  might  be
              equally sensitive, such as user bin or group staff.

       no_root_squash
              Turn  off root squashing. This option is mainly useful for disk&#8208;
              less clients.

       all_squash
              Map all uids and gids to the anonymous  user.  Useful  for  NFS-
              exported  public  FTP  directories, news spool directories, etc.
              The opposite option is no_all_squash, which is the default  set&#8208;
              ting.

       anonuid and anongid
              These  options  explicitly  set the uid and gid of the anonymous
              account.  This option is primarily useful  for  PC/NFS  clients,
              where you might want all requests appear to be from one user. As
              an example, consider the export entry for /home/joe in the exam&#8208;
              ple  section below, which maps all requests to uid 150 (which is
              supposedly that of user joe).

EXAMPLE
       # sample /etc/exports file
       /               master(rw) trusty(rw,no_root_squash)
       /projectss       proj*.local.domain(rw)
       /usr            *.local.domain(ro) @trusted(rw)
       /home/joe       pc001(rw,all_squash,anonuid=150,anongid=100)
       /pub            (ro,insecure,all_squash)
       /srv/www        -sync,rw server @trusted @external(ro)

       The first line exports the entire filesystem  to  machines  master  and
       trusty.   In  addition to write access, all uid squashing is turned off
       for host trusty. The second and third entry show examples for  wildcard
       hostnames and netgroups (this is the entry &#8216;@trusted&#8217;). The fourth line
       shows the entry for the PC/NFS client discussed above. Line  5  exports
       the  public  FTP  directory  to  every host in the world, executing all
       requests under the nobody account. The insecure option  in  this  entry
       also  allows clients with NFS implementations that don&#8217;t use a reserved
       port for NFS.  The sixth line exports a  directory  read-write  to  the
       machine  &#8217;server&#8217;  as well as the &#8216;@trusted&#8217; netgroup, and read-only to
       netgroup &#8216;@external&#8217;, all three mounts with the &#8216;sync&#8217; option  enabled.

Looks like using the options "**all_squash / anonuid / anongid**" might do the trick in /etc/exports?

---

