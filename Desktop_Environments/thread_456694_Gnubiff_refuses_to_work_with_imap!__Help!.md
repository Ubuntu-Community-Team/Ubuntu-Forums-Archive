---
title: "Gnubiff refuses to work with imap!  Help!"
date: 2007-05-27
forum: Desktop Environments
---

### Post by Stoffer on 2007-05-27
I've been trying for hours and hours to get an applet that'll work with both my Gmail POP3 account and my school IMAP account.  I've narrowed it down to "Mail Notification" and Gnubiff.  Both should work with both accounts, but Gnubiff won't work with the IMAP, and Mail Notification won't work with Gmail.

I'd really like to get Gnubiff working, though.  I've tried every possible configuration in the GUI, but it just tells me "error."  Is there a way to run gnubiff in verbose mode so I can see exactly what the error is?  Is there a config file for Mail Notification so I can try copying over the settings?

Here's the relevant portion of my .gnubiffrc file:

  <mailbox>
    <parameter name="address"                 value="mail.ramapo.edu"/>
    <parameter name="authentication"          value="autodetect"/>
    <parameter name="certificate"             value=""/>
    <parameter name="delay"                   value="10"/>
    <parameter name="error_reset_msgs"        value="false"/>
    <parameter name="file_restore_atime"      value="false"/>
    <parameter name="local_fam_enable"        value="true"/>
    <parameter name="name"                    value="Ramapo"/>
    <parameter name="other_folder"            value="Inbox"/>
    <parameter name="other_port"              value="143"/>
    <parameter name="password_aes"            value="[hex version of my password]"/>
    <parameter name="protocol"                value="imap4"/>
    <parameter name="seen"                    value=""/>
    <parameter name="use_idle"                value="true"/>
    <parameter name="use_other_folder"        value="true"/>
    <parameter name="use_other_port"          value="true"/>
    <parameter name="username"                value="[my username]"/>

Like I said, Mail Notification works for IMAP with similar settings.  The port is 143, and there's no ssl other authentication.

---

### Post by Stoffer on 2007-05-28
I ran gnubiff in console and got the following error:

** (gnubiff:15243): WARNING **: [1] Unable to connect to mail.ramapo.edu on port 143

Same for if I put in the IP address instead of mail.ramapo.edu

---

