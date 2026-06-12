---
title: "Gnome network-manager and DNS"
date: 2006-04-08
forum: Desktop Environments
---

### Post by dbkluck on 2006-04-08
Good day all.  I'm having a bizarre problem with networking on Breezy (though the problem existed in Hoary too).  the situation is thus:  i'm currently in beijing, with a VERY restrictive isp (surprise surprise).  i am required to use a static, private IP as well as the isp's dns servers.  in addition, the system uses a no-cat like thing wherein the first web page i ask for redirects to a login screen where i submit a username and password.  however, at boot-up or resumption from suspend, the redirect does not work.  any web page that i attempt to load immediately reports "The browser was unable to connect to the specified site, even though it exists. This may be because the site does not accept connections from your computer, the service may be down, or the site does not support the service or port that you tried to connect to."  attempting to enter the address of the no-cat-like login page directly yields the same result.  pinging anything (even just pinging ips directly without using dns) gives "network is unreachable." /etc/init.d/networking restart and ifupdown eth0 both do not solve the problem.  the ONLY thing that seems to work is going to gnomes system>administration>networking applet, typing the root password, selecting the DNS tab, adding a new DNS server then immediatly deleting it (note that i've made no net change to the settings here) and pressing okay.  after this little charade, everything is hunky dory.  Since i've changed absolutely no settings in this procedure, merely tricked the gnome network-admin applet into reinitializing my current configuration, I would like to find out exactly what commands it is that gnome network-admin calls when dealing with dns so that i might get to the bottom of this.  any thoughts would be much appreciated, 'cause i'm stumped.

---

### Post by dermotti on 2006-04-08
Paragraphs please :-)](*,)

---

### Post by captylor on 2006-05-23
I think what he means is that the DNS entries disappear from /etc/resolv.conf after a computer has been brought out of suspension or hibernation. I am facing this problem as well, and would appreciate any feedback on how to prevent this from happening.

Currently, everytime I "un-suspend" my laptop, I need to manually key in the DNS servers again before I can start accessing the Internet.

---

### Post by Danepak on 2006-05-23
[QUOTE=captylor]I think what he means is that the DNS entries disappear from /etc/resolv.conf after a computer has been brought out of suspension or hibernation. I am facing this problem as well, and would appreciate any feedback on how to prevent this from happening.

Currently, everytime I "un-suspend" my laptop, I need to manually key in the DNS servers again before I can start accessing the Internet.[/QUOTE]


I too am having exactly the same problem, I know what my DNS settings should be but every 10 mins they are reset and overwritten by my ISP's default DSN server settings which are not working today for some reason.

How do I make the change the DNS server permanently?

---

