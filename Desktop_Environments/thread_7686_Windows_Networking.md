---
title: "Windows Networking"
date: 2004-12-09
forum: Desktop Environments
---

### Post by sbaker33 on 2004-12-09
I really need to be able to browse shares, mount network drives and print to Windows printers in order to be able to use UBUNTU as my primary system.  The Windows network consists primarily of a standalone Win2000 server.  So far I have been completely unsuccessful doing so with Linux, with the exception of Xandros and to a lesser extent MEPIS (using smbk4).  

Can anyone provide me a quick and easy explanation of what I need to do to make this work?  Or provide a link to such information?

---

### Post by FLeiXiuS on 2004-12-09
Be aware that the search tool is very powerful.

SAMBA / Smbfs is what your looking for to mount networked drives.

---

### Post by sbaker33 on 2004-12-10
[QUOTE=FLeiXiuS]Be aware that the search tool is very powerful.

SAMBA / Smbfs is what your looking for to mount networked drives.[/QUOTE]

Thanks, I wasn't  aware of that ;-) 

Both are installed and I still have issues and questions (although I was able to connect to the print share last night after my post).

Doing a search on both terms returns about 20 hits.  Most (over half) are about setting up UBUNTU as a SAMBA server.  This doesn't apply.  I am trying to access Windows files shares from UBUNTU not the other way around.  The remainder , many of which are asking the same sort of question I am have no responses.  There are a couple of somewhat useful discussions of a bug in GNOME that causes issues but not final word on a resolution or an effective work around.  

I had already added the appropriate entry for workgroup and WINS server.  I can browse and see the various Windows boxes on my network.  However when I double click on them I get a long wait followed by an error that is consistent with others have reported.  If I try to attach to the share through the menu options I get a permanent hourglass equivalent.  I would like to be able to browse and mount Windows shares through the/a UI.  Is that possible?  Some posts (out of Hoary mainly) seem to make me believe that it may be.

For myself I can probably use the command line but others who use this PC (wife and daughter) will not.  Howwever I am facing a pretty steep hill on that front as well.  I have tried the man pages and help for the mount command but these are extremely difficult to work through for a newbie like myself.  There are long lists of options but little or no information on proper syntax.  Seeing some of the other posts I was able to copy and modify a mount command that partially worked.  However I was only able to see the share in the root terminal.  and don't have a clue what I did wrong.  Can anyone direct me to a good source to learn what I am doing wrong?

Other threads are great sources of information but when you lack context and some basic knowledge they can confuse more than clarify.

---

### Post by FLeiXiuS on 2005-01-09
mount -t smbfs -o username=guest,password="" //ip/sharename /path/to/mount

---

### Post by bobalien on 2005-01-19
[QUOTE=FLeiXiuS]mount -t smbfs -o username=guest,password="" //ip/sharename /path/to/mount[/QUOTE]

I have experienced the same woes as this thread's creator, and had gotten as far as mounting thru the terminal (as suggested above) however I still have some further troubles -

I'm the default IT guy at my office (read: I know the most about computers, so therefore I have to fix the printer, etc) and I'm trying to set up a couple of Ubuntu systems as inexpensive pc's for interns to use.  We're running a Win2k Server with a domain and users set up for basic small office file/printer sharing purposes.

In Ubuntu, under my General network settings tab, I've got cpu6 for hostname, and our network's Domain name (minus the .COM used in Windows) under Host Settings, and I've installed samba and enabled Windows Networking, and filled in the same network Domain here as well.

When I browse Network in the GUI, I can see our main server as well as a handful of other WinXP systems that are on the domain.  If I try to open any of these systems I get a permissions error.

If I "connect to server..."  and enter the IP of the server and a proper User Name, I get a long wait, usually capped by a permissions error.

I tried mounting manually earlier today to some success.  After opening a terminal and performing:

mount //ip.address/share /local/dir/ -t smbfs -o username=myusername,password=mypassword

I was able to successfully mount shares from the server and from my WinXP laptop, but only with Read-Only privaleges (even though I'd logged in using full access user name / passwords) - I could play mp3s from my laptop and view some pdf's from our server, but could not save or copy to either.  Also, it appears these mounts are cleared upon a system restart.

I am looking for a solution like that of the original poster, in that I'm looking to be able to browse the network thru the GUI, or at the very least automate drive mounting (preferably based on a login), as these systems are intended to be used by what will most likely less technically apt individuals than myself.  It looks as if the means to do this are in place in the OS, but I can't seem to configure them properly to get the job done.  Any further help in this area would be extremely appreciated, as I've exhausted many other sources for searching for more detailed information on this topic.

---
Edit: 1/19/05 - 6:48pm

Something I just stumbled on to: I set up a user for the Ubuntu box (username = cpu6) in Active Dir, set the appropriate permissions on a folder "Clients" and I was able to smbclient into //servername/Clients, create and delete directories, etc - my permissions were granted VIA AD properly, but all work was being done thru smbclient from the terminal.  Thinking my previous problem was incorrect permissions in Windows, I tried to mount -t smbfs //servername/Clients to a directory on my Desktop, using my cpu6 user and password, but again received Permissions errors when trying to copy to or create files in this directory. [frowny face]

---
Edit: 1/20/05 - 1:21pm

I tried doing a Connect to Server... thru Nautilus, filling in smb://ip.address for my Server, the share "Clients" for Share, and the AD user name I created for cpu6 as username - this time (I must not have been entering in the ip or username before) I was asked for a password, and developed a false sense of accomplishment as I soon got the error: Nautilus cannot display smb://cpu6@smb/192.168.1.10/Clients

So, in summary I can "mount" thru Terminal to a folder on the desktop (mounting shares off server and my laptop), but only gain Read-Only access.  I can smbclient into the server, and get full access.  Browsing through the Windows Network gives me permissions errors when trying to enter past the top level of any devices (the server, my laptop, etc).  Connect to Server... yields the previously mentioned "cannot display" error.

---
Edit: 1/20/05 2:56pm

The saga continues - if I do a right click on a folder and say Browse folder, bringing up the File Browser (which I have no idea how to get to any other way than this), I can enter smb://domainname/Share, it prompts me for User/Domain/Pass, and then VOILA, I have full access to the folder.  However, it's still requesting authentication each Share I go to, and this still doesn't let someone save from OpenOffice or do much else but create and delete folders from within the file browser.

I still don't know what I'm doing wrong... or doing right.

---

### Post by bobalien on 2005-01-23
[http://ubuntuforums.org/showthread.php?t=12306](http://ubuntuforums.org/showthread.php?t=12306)

found a working solution

---

