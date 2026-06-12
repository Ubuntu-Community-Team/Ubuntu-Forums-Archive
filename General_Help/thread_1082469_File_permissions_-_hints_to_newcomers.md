---
title: "File permissions - hints to newcomers"
date: 2009-02-27
forum: General Help
---

### Post by SteveHillier on 2009-02-27
As many of you know, I am not a newcomer to this Linux game.  I have been around it for some years now but really serious ever since I installed Dapper Drake way back.
I thought I had a grasp of file permissions but an occurrence the other day makes me feel I should quiz this forum, not only for my benefit but also for those who are not very experienced.
I was setting up a virtual host on a LAMP server.  I don't think the fact that it was on Fedora should a) make any differnece to the problem or b) make this thread invalid.
This was not the first time I had used this method to create a virtual hosted web site but let me start from the beginning.
I set up a new user and gave them appropriate group memberships including membership of the ftp group so that I could upload the files.  
I created in that users home folder two directories 'www' and 'log'.
I created the virtual host in httpd.conf by copying an existing host entry and making the appropriate changes.  The document root was pointing to /home/username/www.  The log entries were pointing to /home/username/log.
I restarted the apache server - all OK
I set up the DNS on the local Win 2003 domain server - used for other similar sites hosted within our network.  I could ping the domain name and it would respond back to the right IP address.
I then developed a simple web page on the workstation and used FileZilla client to upload the file to the site.  Checking on the server that worked OK.
I then tried to http into the site and got an 403 - permissions denial.  I checked the log, it recorded that there had been an access issue.
I checked the permissions on the www directory.  The owner was identical to another site that was working.  The group also the same.  The permissions were set to 755, just like the other sites that worked.
I checked the permissions on the files within the www folder.  There seemed to be no difference between the ownership, group access of user access on any of these files from other working sites.
After about 2 hours of exploring this, even setting it all up again from scratch with different names, checking and rechecking httpd.conf entries, files permissions, dns settings nothing would make this work.
I worked back through notes I had made when creating previous sites.  It made no difference.
Eventually, and I don't even know why I looked at it, I looked at the /home/username directory and found the permissions were set to 750.  I changed this to 755 and hey presto everything worked.
So my question to all those who know about these thing is this.
Why is it that even when the permissions on the folder containing the web files had been explicitly set to allow read and execute rights to others did the more restrictive permissions of the parent directory kick in?

Apologies - I seem to have used folder and directory interchangably - I have been around Windows too long!

---

### Post by leewebb on 2009-02-28
> **SteveHillier said:**
> 
Eventually, and I don't even know why I looked at it, I looked at the /home/username directory and found the permissions were set to 750. I changed this to 755 and hey presto everything worked.
So my question to all those who know about these thing is this.
Why is it that even when the permissions on the folder containing the web files had been explicitly set to allow read and execute rights to others did the more restrictive permissions of the parent directory kick in?


Because to get to /home/username/log you have to first access (or "read" via the execute permission of the directory) /home/username, and to get to /home/username, /home must have the correct (other) permissions for reading as well. 

Remember that for directories, the permissions are slightly different compared to files. Out of r (read), w (write), x (execute) you have:

Files:
r = can view the file
w = can write to the file
x = can run the file

Dirs:
r = you can list the contents of the directory (but can't cd into it without the execute bit set)
w = you can create a file in the directory
x = you can enter (cd into) the directory

---

