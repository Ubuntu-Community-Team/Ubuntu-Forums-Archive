---
title: "Ubuntu 8.10 Active Directory Membership Issues"
date: 2009-03-08
forum: General Help
---

### Post by GPollos on 2009-03-08
Hi,

I recently joined my Ubuntu box to my domain but I'm running into a bit of an issue. I used the Likewise software to join, my nsswitch.conf is properly configured to my knowledge. When I try to login with any of my domain accounts however, it tells me that authentication has failed and that it could not set my user group. I tried logging in with a domain acct with a password close to expiry and it notified me that my password was expiring but then gave me the "auth failed, cannot set user group" message.

Also, when I check my event logs on the DC, it has events for failed logins, the attempts I made to login from the linux box. I had attempted to join the domain previously using the instructions [here]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"). I didn't clean up after that attempt, could this greatly affect using likewise to join the domain?

Any ideas why this would happen? What files should I be reading and poking around in to make this work? Your help is greatly appreciated.

Thank you,
GPollos

---

### Post by HermanAB on 2009-03-08
It worked before? Then it should keep working.

Check the time and ensure that the client is within 5 minutes of the server.  Dailight savings changed today in North America.

Look at your log files in /var/log to see what happens when you try to join and log in.

Cheers,

Herman

---

### Post by GPollos on 2009-03-08
Actually, no. When I attempted to use that guide that I linked to, I only got as far as getting a kerberos ticket. Otherwise, it didn't work.

The clocks are sync'd. I'm in Ontario so my clocks changed and are all fine. Just FYI, my domain and forest are at a Windows 2003 functional level if that has any major bearing on linux clients joining.

Here is the relevant section of my /var/log/auth.log:
Mar  8 14:20:50 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): PAM config: global:krb5_ccache_type 'FILE'
Mar  8 14:20:50 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): failed to get GP info
Mar  8 14:20:50 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): getting password (0x00000000)
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): enabling krb5 login flags
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): enabling cached login flag
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): enabling request for a FILE krb5 ccache type
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:auth): request failed: Logon failure, WBL error was Logon failed due to bad username or password (6), NT error was NT_STATUS_LOGON_FAILURE, PAM error 7
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): PAM config: global:krb5_ccache_type 'FILE'
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): No membership check being enforced
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): Returning 0 for user "andrew"
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): user 'andrew' granted access
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): homedir is /home/BEMBRIDGE/andrew
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:account): Missing UPN for user 'andrew'
Mar  8 14:20:53 bemb-andrew-ub sudo:   andrew : TTY=unknown ; PWD=/home/andrew ; USER=root ; COMMAND=/usr/bin/domainjoin-gui
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:setcred): PAM config: global:krb5_ccache_type 'FILE'
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:setcred): request failed
Mar  8 14:20:53 bemb-andrew-ub sudo: pam_lwidentity(sudo:setcred): User 'root' is not known.

What is interesting though, is when I join the domain with likewise, it succeeds and tells me the box is now on the domain, the event log on my DC also show a successful auth and creation of a computer account for bemb-andrew-ub. However, I notice an event that tells me that pre-auth failed @ 2:29:05 PM. Which is the time I re joined the domain to get proper logs.
Pre-authentication failed::

 	User Name:	bemb-andrew-ub$

 	User ID:		BEMBRIDGE\bemb-andrew-ub$

 	Service Name:	krbtgt/BEMBRIDGE.LOCAL

 	Pre-Authentication Type:	0x0

 	Failure Code:	0x19

 	Client Address:	192.168.2.22

---

### Post by GPollos on 2009-03-08
Ok, So I rolled back the clock. I uninstalled all the relevant packages that I had used in different tutorials. I left the domain, uninstalled kerberos support and likewise, etc. deleted the config files and then reinstalled. I joined the domain successfully and took a look at my event logs on the DC. It seems kerberos pre authentication is failing at every attempt this machine makes to auth and do something. Both the users I log on with and the comptuer account bemb-andrew-ub fail pre authentication. The pre auth type listed in the fail log claim pre auth types 0 and 2 fail with failure codes 19 and 18 respectively.

I'm not sure if it's just AD or its something on this end. Any suggestions?

---

