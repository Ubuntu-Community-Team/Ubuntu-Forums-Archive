---
title: "Problems with Mutt and GetLive"
date: 2009-05-19
forum: General Help
---

### Post by ooolongT on 2009-05-19
I am having trouble setting up GetLive in Mutt.  I have searched, but I can not seem to find any information about this problem in particular. The problem looks like this when I run it manually from the command line: 

```
GetLive $Revision: 1.48 $ Copyright (C)2007-2009 Jos De Laender.
GetLive comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; see the file License for details.
$Name:  $
$Id: GetLive.pl,v 1.48 2009/02/14 19:34:13 jdla Exp $
Running at Tue May 19 18:51:37 2009 for user [COLOR="Red"]myusername[/COLOR].
Logging in.
Got MainPage.

Processing folder Inbox.
Loading folder 'Inbox'.
126/48 Messages/Unread.
GetLive died with message: 'Could not open ~/.getlive.log : No such file or directory. at /usr/bin/getlive line 1220.
'.You have new mail in /var/spool/mail/tj

```

It looks like this when Mutt runs it as a cron job:

```
This is free software, and you are welcome to redistribute it
under certain conditions; see the file License for details.
$Name:  $
$Id: GetLive.pl,v 1.48 2009/02/14 19:34:13 jdla Exp $
Running at Tue May 19 20:05:01 2009 for user .
Usage: GetLive --config-file ConfigFile [--verbosity -1..100]

```

It appears that the PERL script getlive is looking for a file that does not exist. However, I made that file. and it is in my home directory:
```

tj@tj-desktop:~$ ls -la  
.
.
.                                                                    
-rwxrwxrwx  1 [COLOR="Red"]myusername[/COLOR]   [COLOR="Red"]myusername[/COLOR]       1 2009-05-19 17:04 .getlive.log                                

```

Here are the lines from the getlive PERL script:
```
########################################################################################################################
# 
# Process the messages retrieved from a folder.
# Acts on global variables @Messages ...
# It just takes FolderIdx for knowing the name. (and now also for the MoveToFolder/Delete command)
# 
########################################################################################################################

sub ProcessMessagesFromFolder ($) {
  my ($FolderIdx) = @_;
  my $FolderName = $FolderNames[$FolderIdx];
  # Now let's run through all detected messages ..
  my $MessageIdx;
  for ($MessageIdx=0;$MessageIdx<$NrMessagesDetected;$MessageIdx++) {
    if ($DownloadedIdsFile) {
      # First we check and or create the file with the downloaded Ids.
      if (not -e $DownloadedIdsFile) {
        open (DOWNLOADED,">$DownloadedIdsFile") || die "Could not open $DownloadedIdsFile : $!.";
        print DOWNLOADED "-- This is an automatically generated file by $0 containing the id of downloaded messages\n";
        close (DOWNLOADED);
      }
```
 (you can view the whole file [here.]("http://getlive.cvs.sourceforge.net/viewvc/*checkout*/getlive/GetLive/GetLive.pl"))
Can anyone tell me what is wrong?

Thanks!

---

### Post by andrew.46 on 2009-05-20
Hi ooolongT,

> **ooolongT said:**
> 
```

tj@tj-desktop:~$ ls -la                                                                    
-rwxrwxrwx  1 [COLOR="Red"]myusername[/COLOR]   [COLOR="Red"]myusername[/COLOR]       1 2009-05-19 17:04 .getlive.log                                

```


I will confess to a complete lack of any knowledge concerning GetLive but I wonder if this the same problem that you experienced with your mutt setup? If so it *should* be set right by altering the permissions as an ordinary user:

```
chmod 0644 $HOME/.getlive.log
```

Although you may need to adjust *ownership* as well. It is a little odd that some of your files are set as 0777 though...

Andrew

---

### Post by ooolongT on 2009-05-20
Andrew, thank you once again for your help.  Apparently, the permissions are not the culprit this time.  I changed the permissions as you suggested, and then checked the ownership (I am the owner), all to no avail.  


I feel like you are on the right track though, there is some setting that needs to be changed somewhere, but for the life of me, I can't figure out which one.  ](*,)

---

### Post by andrew.46 on 2009-05-20
Hi ooolongT,

> **ooolongT said:**
> Andrew, thank you once again for your help.  Apparently, the permissions are not the culprit this time.  I changed the permissions as you suggested, and then checked the ownership (I am the owner), all to no avail.  

I am afraid that I am no help to you here then, I am not familiar with this program. But the forums are big and hopefully there is an eager GetLive user here somewhere!

All the best,

Andrew

---

