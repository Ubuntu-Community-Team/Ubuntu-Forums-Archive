---
title: "sshd mysteriously won't start after reboot"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Blueshell on 2006-01-09
I have a Breezy which I just rebooted, and discovered that sshd isn't getting restarted.  Its got a virtual twin which doesn't have this problem, but doing things like diffing /etc across the two machines hasn't helped me figure this out.

I tried adding, e.g. ``echo "$1" >> /etc/sshdebug'' to /etc/init.d/ssh (and creating that file, of course), and discovered that, on the machine that still works, ssh gets called with "stop" on shutdown and "start" on boot, but on the failing machine, it only gets called with "stop" on shutdown, e.g., it's never being asked to start.  Other services on the machine appear to be getting started, and if I just run /etc/init.d/ssh start by hand, sshd starts up just fine.

Doing "wc rc*/*ssh*" while in etc gives me six identical answers which all correspond to the length of /etc/init.d/ssh, so the symlinks there are fine.

/etc/inetd.conf is zero-length on both machines.  On a third Breezy, it's not even present.  On a Hoary, it's got contents, but every line is commented-out.  (I haven't edited any of these four files; I find it curious that they're not all either zero-length or all filled with commented-out text).

Where should I be looking?  (And, of course, why did this change spontaneously? But I assume I'll figure out the latter if I can figure out the former...)

Thanks.

---

### Post by timfrost on 2006-01-09
What is the result of
```

ls /etc/rc?.d/*ssh*

```
on the two machines?

---

### Post by Blueshell on 2006-01-09
Well, I said that wc on them worked fine, but here's the result for running ls -alF /etc/rc?.d/*ssh* on each:

Working case:

lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc0.d/K20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc1.d/K20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc2.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc3.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc4.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc5.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc6.d/K20ssh -> ../init.d/ssh*

Broken case:

lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc0.d/K20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc1.d/K20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc2.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc3.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc4.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc5.d/S20ssh -> ../init.d/ssh*
lrwxrwxrwx  1 root root 13 Nov  5 14:56 /etc/rc6.d/K20ssh -> ../init.d/ssh*

I sure don't see a difference, or anything wrong, either.

---

### Post by timfrost on 2006-01-09
Confirm that the init.d script is there, and OK:

ls -l /etc/init.d/ssh

md5sum /etc/init.d/ssh

---

### Post by Blueshell on 2006-01-09
I already said that the init script -does- run when stopped.

However, just for yucks, here are directory listings of the working and nonworking machines, and their md5sums.  The .VIRGIN files are the ones I started with, before inserting debugging statements to see which got called when.

Is there any way of asking init to provide debugging info on which scripts it's trying to run?  For that matter, is it actually init that's running these scripts in the first place?

Working:

-rwxr-xr-x  1 root root 2044 Jan  9 19:28 ssh*
-rwxr-xr-x  1 root root 2016 Oct 10 16:10 ssh.VIRGIN*
-rwxr-xr-x  1 root root 2016 Oct 10 16:10 ssh~*

ec7d28155f2f06c1e89d701376fae2e5  ssh
de055363f076533138850c2837677338  ssh.VIRGIN
de055363f076533138850c2837677338  ssh~

Broken:

-rwxr-xr-x  1 root root 2510 Jan  9 19:16 /etc/init.d/ssh*
-rwxr-xr-x  1 root root 2016 Oct 10 16:10 /etc/init.d/ssh.VIRGIN*
-rwxr-xr-x  1 root root 2453 Jan  9 19:09 /etc/init.d/ssh~*

59037389c1c208cad2b69a5621ca533b  ssh
de055363f076533138850c2837677338  ssh.VIRGIN
06ced1a83fbefe881ab603f9f3caccc8  ssh~

---

### Post by ape on 2006-01-09
Verify that you don't have a file called sshd_not_to_be_run living in the /etc/ssh directory. If you do, remove it, then issue `sudo /etc/init.d/ssh start`.

Also make sure that your /usr/sbin/sshd file is executable.

---

### Post by Blueshell on 2006-01-09
I did both of those when I first started debugging, since reading the script indicated it looked for that file.  It's not present.  (And what in the world might have automatically -created- such a file?)

And this sure looks like the binary is executable:

-rwxr-xr-x  1 root root 278492 Oct 10 16:11 sshd

Remember, I said that (a) the script -was not being called with "start" on boot even though it was being called with "stop" on shutdown, (b) if I run "/etc/init.d/ssh start" by hand, sshd comes up just fine (so the script itself works, and the binary works, and the don't-run file must not be present), so the problem is -not- either the script or the binary, but the fact that init (or whatever is supposed to be calling it) is apparently NOT calling it with "start" when it starts incrementing runlevels!

As I said, I'm stumped.

---

### Post by ape on 2006-01-10
Definitely a strange one.  Have you tried booting up with as much verbosity as possible to see if there are any error messages that are getting swallowed somehow?

I'd do two things here:

1. Edit your /boot/grub/menu.lst file and remove the quiet argument on your particular kernel boot entry.

2. Edit the /etc/init.d/ssh script and remove the --quiet argument from the start-stop-daemon entries.

Reboot the machine and see if there is any more info that comes up when/if ssh is attempted to be loaded.

---

### Post by Blueshell on 2006-01-10
I tried doing both of these, but didn't see any real increase in logging verbosity.  None of the logs in /var/logs even have the string "ssh" in them; should some?  Should I be looking elsewhere?

(In particular, I removed the "quiet" from my 2.6.12-10 kernel line, since that's the kernel the machine is booting; I saw a slight change in the stuff it splashes while booting (I don't remember the exact added phrase at this point), and I've also been alternating boots with the recovery-mode stanza, which doesn't have quiet in the first place.)

I removed all the --quiet's in the ssh script that's getting run, but of course the problem there is that it doesn't seem to be called on boot at all.

I also created (a while ago) another script called ssh-again which just echoed $1 to my debugging file and did nothing else, and then used "update-rc.d ssh-again  default 21" to install it (just after the 20 where ssh normally sits).  That script, too, doesn't seem to be getting called on boot---only on shutdown:  it only ever seems to write "stop" into my debugging file.

And I -thought- that other services were up because I thought it was serving NFS (which starts just after ssh), but it turns out that it's not doing that, either.  I'll carefully try to enumerate which services it seems to be running, if any, but it's beginning to look at though init simply isn't running several/most/all of the scripts.  (Yet the window system comes up just fine and it claims to be setting time from the network and so forth when it boots, etc etc---a boot at the console looks just perfect, and I'd imagine if it's failing to run most of these scripts that all sorts of things wouldn't be working, hence my confusion; I'm going to take a more careful look at that next, now that I've realized NFS isn't actually up either.)

Any way to debug what init thinks it's doing?  Am I correct in believing that it's init's job to run all these scripts?

---

### Post by Blueshell on 2006-01-10
The plot thickens:  It definitely looks like init is wedging somehow.

On the working machine, "ps -elf | grep [i]nit" looks like this:

4 S root         1     0  0  76   0 -   390 -      Jan09 ?        00:00:00 init [2]

...but on the broken machine, it looks like this:

4 S root         1     0  0  76   0 -   390 -      02:41 ?        00:00:00 init [2]
4 S root      6325     1  0  76   0 -   647 wait   02:42 ?        00:00:00 /bin/sh /etc/init.d/rc 2
1 S root      7281  6325  0  78   0 -   647 wait   02:42 ?        00:00:00 /bin/sh /etc/init.d/rc 2

What the heck are those extra two init processes, both apparently talking about runlevel 2, doing there?

I may see if lsof can tell me what files they have open, which might lend a clue...

---

### Post by Blueshell on 2006-01-10
Okay, I think I fixed it.  Get a load of this:

I've been running an experimental server out of one of the entries in init.d that used to get invoked like this:

su - some-user "the-server  > /some/dir/logfile.$$"

The server daemonizes after launch.

But since it produces really giant logs, I decided to change this to:

su - some-user "the-server | split -d -l 500000 - /some/dir/logfile.$$."

and apparently -now- the server does NOT daemonize!  It just sits there, running in the foreground, preventing the script from finishing, and hence preventing init from running anything farther in that runlevel.  And since the script doesn't do all the "Starting foo...  Stopping foo" stuff of a normally written script (it's just a couple lines), there was no visible evidence that it was hanging, and hence no visible evidence that init was hanging, either.  (Apparently the things it starts afterwards don't actually produce lines to the console when they start, and also apparently the machine had been up so long that any logfile mentioning sshd (which -does- at least write a log to auth.log when it starts, but not to the console)  had been rotated away and deleted, which was why I didn't even find any lines in /var/log that mentioned sshd.  (-Now- it says "sshd[pid]: Server listening on :: port 22." in auth.log))

I have no idea why bash apparently gives dramatically different results in this case when switching from output redirection to a pipe; how can the process producing the output even -know-?  In any event, putting a & at the end of the line just before the closing quote fixed it, since it forces everything into the background.  (This would be bad if the script actually produced output indicating it was starting/stopping things, because any errors would get lost and not sent to the console, but it doesn't.)

This all became pretty instantly obvious once I found those wedged inits, because lsof immediately told me that  one of the rc processes still had that script open, which immediately pointed the finger.

If anyone can tell me why a process that normally daemonizes can fail to do so when changing from redirection to a pipe, I'd love to hear it.

---

### Post by ape on 2006-01-10
Good investigation!  

Can you verify that it is a generic pipe issue or just a pipe to `split`.  Since you are telling split to read from standard input, there may be something going on there.  i.e. do you get the same result of non-daemonization regardless of which program you are piping to?

---

