---
title: "Security breach on the Ubuntu Forums."
date: 2013-07-30
forum: Forum Feedback &amp; Help
---

### Post by Elfy on 2013-07-30
> As announced previouslyA¹, there was a security breach on the Ubuntu
Forums.  What follows is a detailed post mortem of the breach and
corrective actions taken by the Canonical IS team. In summary, the
root cause was a combination of a compromised individual account and
the configuration settings in vBulletin, the Forums application
software.  There was no compromise of Ubuntu itself, or any other
Canonical or Ubuntu services.  We have repaired and hardened the
Ubuntu Forums, and as the problematic settings are the default
behaviour in vBulletin, we are working with vBulletin staff to change
and/or better document these settings.

== What happened ==

At 16:58 UTC on 14 July 2013, the attacker was able to log in to a
moderator account owned by a member of the Ubuntu Community.

This moderator account had permissions to post announcements to the
Forums. Announcements in vBulletin, the Forums software, may be
allowed to contain unfiltered HTML and do so by default.

The attacker posted an announcement and then sent private messages to
three Forum administrators (also members of the Ubuntu community)
claiming that there was a server error on the announcement page and
asking the Forum administrators to take a look.

One of the Forum administrators quickly looked at the announcement
page, saw nothing wrong and replied to the private message from the
attacker saying so.  31 seconds after the Forum administrator looked
at the announcement page (and before the administrator even had time
to reply to the private message), the attacker logged in as that Forum
administrator.

Based on the above and conversations with the vBulletin support staff,
we believe the attacker added an XSS attack in the announcement they
posted which sent the cookies of any visitor to the page to the
attacker.

Once the attacker gained administrator access in the Forums they were
able to add a hook through the administrator control panel.  Hooks in
vBulletin are arbitrary PHP code which can be made to run on every
page load.  The attacker installed a hook allowing them to execute
arbitrary PHP passed in a query string argument.  They used this
mechanism to explore the environment and also to upload and install
two widely available PHP shell kits.  The attacker used these shell
kits to upload and run some custom PHP code to dump the 'user' table
to a file on disk which they then downloaded.

The attacker returned on 20 July to upload the defacement page.

== What the attacker could access ==

The attacker had full access to the vBulletin environment as an
administrator and shell access as the 'www-data' user on the Forums
app servers.

Having administrator access to the vBulletin environment means they
were able to read and write to any table in the Forums database.

They used this access to download the 'user' table which contained
user names, email addresses and salted and hashed (using MD5)
passwords for 1.82 million users.

== What the attacker could not access ==

We believe the attacker was NOT able to escalate past the 'www-data'
user (i.e. gain root) access on the Forums app servers.

We believe the attacker was NOT able to escalate past remote SQL
access to the Forums database on the Forums database servers.

We believe the attacker did NOT gain any access at all to the Forums
front end servers.

We believe the attacker was NOT able to gain any access to any other
Canonical or Ubuntu services.

We know the attacker was NOT able to gain access to any Ubuntu code
repository or update mechanism.

== What we don't know ==

We don't know how the attacker gained access to the moderator account
used to start the attack.

The announcement the attacker posted was deleted by one of the Forum
administrators so we don't know exactly what XSS attack was used.

== What we've done ==

Before bringing the Forums back online, we implemented a series of
changes both designed to clean up after this attack and also to defend
against and mitigate the fallout from possible attacks in the future.

=== Clean up ===

 * We sent individual mails to all Forums users informing them of the
   breach and that they should consider their Forum password
   compromised.  We advised them to change this password on any other
   systems where they may have re-used it.

 * We backed up the servers running vBulletin, and then wiped them
   clean and rebuilt them from the ground up.

 * We randomised all user passwords in the Forums.

 * We reset all system and database passwords.

 * We manually imported data into a fresh database after sanity
   checking each table.

=== Hardening ===

 * We've removed the ability to modify or add new hooks except via
   root access to the database

 * We've disabled all potential HTML posting avenues in the Forums for
   everyone but administrators.

 * We've switched the Forums to use Ubuntu SSO for user
   authentication.

 * We've implemented automated expiry of inactive moderator and
   administrator accounts.

 * We've confined vBulletin with an AppArmor profile.

 * We've reviewed and further hardened the firewalling around the
   Forums servers.

 * We've reviewed and further hardened the PHP config on the server to
   close off some vectors used by the attacker.

 * We've switched to forcing HTTPS for the administrator and moderator
   control panels and made it optionally available everywhere else

 * We've improved escalation procedures for the Ubuntu Community
   members who graciously volunteer their time to administer and
   moderate the Forums.

 * We will continue to work with vBulletin staff to discuss changes to
   the default settings which could help others avoid similar
   scenarios as this.  The vBulletin support staff have been helpful
   and cooperative throughout this incident.

Finally, we'd like once again to apologize for the security breach,
the data leak and downtime.

--
A¹ [http://blog.canonical.com/2013/07/21/notice-of-security-breach-on-ubuntu-forums-site/](http://blog.canonical.com/2013/07/21/notice-of-security-breach-on-ubuntu-forums-site/)

Copy of Canonical announcement. Link to Canonical Blog [here]("http://blog.canonical.com/2013/07/30/ubuntu-forums-are-back-up-and-a-post-mortem/").

---

