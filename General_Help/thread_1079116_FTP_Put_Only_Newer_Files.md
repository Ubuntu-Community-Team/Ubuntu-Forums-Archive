---
title: "FTP Put Only Newer Files?"
date: 2009-02-24
forum: General Help
---

### Post by veaudaux on 2009-02-24
I'm looking to set up an automated script to FTP the contents of a directory to a remote server via a cron job.

It works fine, except for the fact that entire contents get transferred every time - I'd really like to find a way to upload only files that have changed since the last transfer.

The built-in ftp command "newer" does what I want, except in the wrong direction ('newer' GETs, I want to PUT).

If anybody knows of a client that can support this kind of thing at a command line scripting level, or has an idea how to make this work, I'd be eternally grateful.

---

### Post by prshah on 2009-02-24
> **veaudaux said:**
> I'm looking to set up an automated script to FTP the contents of a directory to a remote server via a cron job.

Have you considered using rsync? It will do the job much, much faster and includes the features you are looking for of transferring only the changed files.

Please see the man page for rsync for usage, or post back if you want more details.

---

### Post by veaudaux on 2009-02-24
> **prshah said:**
> Have you considered using rsync? It will do the job much, much faster and includes the features you are looking for of transferring only the changed files.

Please see the man page for rsync for usage, or post back if you want more details.

Thanks for the response!

I have considered rsync, but unfortunately, the remote server doesn't support it.

---

### Post by kirangv22 on 2009-02-25
#! /bin/sh
    # /etc/init.d/blah
    #

    # Some things that run always
    touch /var/lock/blah

    # Carry out specific functions when asked to by the system
    case “$1&#8243; in
    start)
    HOST=’10.147.251.90&#8242;
    USER=’tritech’
    PASSWD=’tritech’
    ftp -n $HOST <<END_SCRIPT
    quote USER $USER
    quote PASS $PASSWD
    get candle1.C
    END_SCRIPT
    ;;
    stop)
    echo “Starting script blah ”
    ;;
    *)
    exit 1
    ;;
    esac

    exit 0

    this is my script in which i am trying to copy the file candle1.C from an ftp server at the time of starting the system so i had put this file in /etc/init.d/blah .but it is not working , instead of these ftp commands if am using mkdir d something like command it is working means this script is working but for using an ftp what i have to do , or it is possible to start an ftp connection at the time of init process.plz help me.

---

### Post by veaudaux on 2009-02-26
I found a solution - basically what this will allow me to do is a local rsync that uploads to the remote FTP server.

First of all, I installed the "curlftpfs" package. curlftpfs allows you to mount a remote FTP filesystem as a local folder.

I created a folder in my home directory called "backups", then ran:
```
sudo curlftpfs ftp.myftpserver.com /home/USERNAME/backups/ -o allow_other -o uid=1000 -o user=FTPUSERNAME:FTPPASSWORD -o nonempty
```

(You will have to replace 'uid' with your user ID. If you only have one account on your computer, chances are it's 1000, but to check, type "id USERNAME" into the terminal).

Now when I navigate to /home/USERNAME/backups/, I see the listing of my remote FTP directory.

For the rsync, I had to create a local directory for rsync to store temporary files. I made mine /var/tmp/rsync/ (I went to /var/tmp/ and created an 'rsync' folder).

Now to sync files:
```
rsync /home/USERNAME/DirectoryToBackup/ /home/USERNAME/backups/DirectoryToBackup/ -vur --temp-dir=/var/tmp/rsync
```

That should upload only changed files to the remote FTP server.

After it's finished, run:
```
sudo umount /home/USERNAME/backups/
```
to close the FTP connection.

---

