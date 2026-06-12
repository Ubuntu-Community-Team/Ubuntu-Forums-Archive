---
title: "OpenVPN on Ubuntu; issues"
date: 2011-03-10
forum: Desktop Environments
---

### Post by MMegaTron on 2011-03-10
Hi Guys,

I'm doing freelance IT Support for a small company.  They have approx 6 users in the office and 3 connecting from home.  The previous IT support guy who I took over from had set-up everybody connecting via SSH, whcich was causing a lot of permissions problems with the shared files.  So I took a friends advice and moved over to a VPN; installing OpenVPN. It seems to work prefectly except for an irritating problem, which is preventing me from migrating everybody over.  I run the OpenVPNserver from the command line  (bash, on ubuntu), because I like to see an error log.  The problem I'm  having is that clients connect fine when connecting to the OpenVPN  server if it's started from the terminal, but whenever the daemon is  running, clients can't connect.  This would be fine if we could just  have the program run from command line all the time.  However, something  that the client is doing is causing OpenVPN (running from the command line) to restart and then revert back to the daemon which then proceeds to stop users from  connecting.  Do you have any ideas what might be causing this or how to  resolve the problem?  

Thanks.

---

### Post by deconstrained on 2011-03-10
> **MMegaTron said:**
> Hi Guys,

I'm doing freelance IT Support for a small company.  They have approx 6 users in the office and 3 connecting from home.  The previous IT support guy who I took over from had set-up everybody connecting via SSH, whcich was causing a lot of permissions problems with the shared files.
When a person is logged in via SSH, the permissions on the remote host to which they connect will appear exactly the same as if they were logged in non-remotely, i.e. at a terminal. Thus, VPN won't change a thing (if permissions of files on the host were what you were referring to).

What you could try doing once you get OpenVPN set up properly is create a Samba or NFS share on the server, which, if configured correctly, would allow users to access the files remotely without permissions problems once they have connected to the VPN. That's what VPN is really good for: allowing remote users to access services and hosts on a private network that would otherwise be inaccessable from the outside due to essential security practices and the limitations of routing/NAT.

> **MMegaTron said:**
> I run the OpenVPNserver from the command line  (bash, on ubuntu), because I like to see an error log.  The problem I'm  having is that clients connect fine when connecting to the OpenVPN  server if it's started from the terminal, but whenever the daemon is  running, clients can't connect.  This would be fine if we could just  have the program run from command line all the time.  However, something  that the client is doing is causing OpenVPN (running from the command line) to restart and then revert back to the daemon which then proceeds to stop users from  connecting.
**My best guess:** the OpenVPN "daemon" on the server end is not using the correct configuration file. If your OpenVPN's server name is 'foo', the keys and configuration file should all be named /etc/openvpn/foo.{conf,crt,key}. *The OpenVPN daemon initscripts of most Linux distros will look in /etc/openvpn for configuration files before starting,* so if your server configuration/keys aren't stored there, they won't be used/loaded when the daemon starts up.

FYI the OpenVPN service does not always have to be started "from the command line" (meaning, invoking the command as superuser and forking to the background) in order to see the log; when OpenVPN runs, the name/path of the log file is specified in the server/client's configuration, and thus it will be written to regardless of how the daemon is started (as long as it uses the same configuration file).

---

### Post by MMegaTron on 2011-03-28
Thanks very much for your input.  I managed to get it sorted in the end by using tail to look at the log while the daemon is running, rather than killing the daemon via pidof and kill, and starting it from the command line.  Yoour post offers some insight though!

---

