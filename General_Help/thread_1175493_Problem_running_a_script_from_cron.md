---
title: "Problem running a script from cron"
date: 2009-06-01
forum: General Help
---

### Post by serpent_slang on 2009-06-01
Hi guys, I have created a Shell Script to synchronized a folder on my local machine to another machine on my network. Following is my script:

#!/bin/sh

RSYNC=/usr/bin/rsync
SSH=/usr/bin/ssh
KEY=/home/<user_name>/myfiles/controller1-rsync-key
RUSER=userID
RHOST=IP-Address
RPATH=/home/<remote_user>/backup_Folder/Folder1
LPATH=/home/<user_name>/backup_Folder/

$RSYNC -az -e "$SSH -i $KEY" $RUSER@$RHOST:$RPATH $LPATH 

When i am running this script from terminal, it is working fine.

---------------------------------------------------------------

In order to regularly call this script, i tried to add this as a cron job. By following methods:

1) open /etc/crontab file and added my script like

*/5 * 	* * * 	root	/home/<user_name>/myfile/sync_script

This should call my script every 5 min. But it's not at all working.

2) I also tried to add the job by:
     crontab -e
and add the script there. 

---------------------------------------------------------------------

Please tell me what i am doing wrong. I am frustrated. Please help

---

### Post by tgalati4 on 2009-06-01
/etc/crontab is used for system-wide cron jobs.

crontab -u yourusername -e  

is used for your personal cron jobs.

Script looks OK.  Perhaps it is a permission/owner issue.  Don't run it as root, but as yourusername.

What is the output of:

crontab -u yourusername -l

Also does /var/log/auth.log say?

It should look something like:  (for a personal cron job started at 7 am this morning)

Jun  1 07:00:01 tubuntu2 CRON[17009]: (pam_unix) session opened for user smmsp by (uid=0)
Jun  1 07:00:02 tubuntu2 CRON[17011]: (pam_unix) session opened for user tgalati4 by (uid=0)
Jun  1 07:01:03 tubuntu2 CRON[17009]: (pam_unix) session closed for user smmsp
Jun  1 07:01:03 tubuntu2 CRON[17011]: (pam_unix) session closed for user tgalati4


From the man page for crontab:

       If the -u option is given, it specifies the name of the user whose crontab is  to  be
       tweaked.   If  this  option  is not given, crontab examines "your" crontab, i.e., the
       crontab of the person executing the command.  Note that *su* can confuse crontab and
       that  if  you  are  running  inside  of *su* you should always use the -u option for
       safety&#8217;s sake.

Finally, from the rsync man page:

       Some modules on the remote daemon may require authentication. If so, you will receive
       a  password prompt when you connect. You can avoid the password prompt by setting the
       environment variable RSYNC_PASSWORD to the password you want  to  use  or  using  the
       --password-file option. This may be useful when scripting rsync.

       WARNING:  On  some  systems  environment variables are visible to all users. On those
       systems using --password-file is recommended.

Do you get a password prompt from the command line when running the script?

Finally, finally, from the crontab man page:

Although  cron requires that each entry in a crontab end in a newline character, nei&#8208;
       ther the crontab command nor the cron daemon will detect  this  error.  Instead,  the
       crontab  will  appear to load normally. However, the command will never run. The best
       choice is to ensure that your crontab has a blank line at the end.

---

### Post by serpent_slang on 2009-06-02
Thanks for the reply, i removed my job from /etc/crontab and have used crontab -u <username> -e

But my auth.log file is showing the following messages:

Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:account): failed to get GP info
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:account): request failed
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:account): User 'owais' is not known.
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:account): Returning 7 for user "owais"
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:session): request failed
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:session): User 'owais' is not known.
Jun  2 11:20:01 ubu CRON[12548]: pam_unix(cron:session): session opened for user owais by (uid=0)
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:setcred): request failed
Jun  2 11:20:01 ubu CRON[12548]: pam_lwidentity(cron:setcred): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:account): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:account): failed to get GP info
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:account): request failed
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:account): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:account): Returning 7 for user "owais"
Jun  2 11:20:56 ubu sshd[12676]: Accepted publickey for owais from 192.168.1.127 port 45873 ssh2
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): request failed
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:session): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:session): request failed
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:session): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_unix(sshd:session): session opened for user owais by (uid=0)
Jun  2 11:20:56 ubu sshd[12683]: pam_lwidentity(sshd:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12683]: pam_lwidentity(sshd:setcred): request failed
Jun  2 11:20:56 ubu sshd[12683]: pam_lwidentity(sshd:setcred): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): request failed
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): request failed
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:setcred): User 'owais' is not known.
Jun  2 11:20:56 ubu sshd[12676]: pam_lwidentity(sshd:session): PAM config: global:krb5_ccache_type 'FILE'
Jun  2 11:20:56 ubu sshd[12676]: pam_unix(sshd:session): session closed for user owais

-------------------------------------------------------------

---

