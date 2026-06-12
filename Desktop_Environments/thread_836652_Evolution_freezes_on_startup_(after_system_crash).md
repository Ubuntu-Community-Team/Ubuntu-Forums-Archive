---
title: "Evolution freezes on startup (after system crash)"
date: 2008-06-21
forum: Desktop Environments
---

### Post by JoeHarr4 on 2008-06-21
The other night my laptop crashed for unknown reasons while I happened to be running evolution.  I don't think the crash had to do with evolution, it was suspend-related.  This has happened before with no problems.  I just reboot, login, and restart evo.  But this time when I logged in and started evolution, it put up my mail reader (as usual) and froze (not usual).  The CPU pegged.  The top program shows evolution to be the top CPU consumer.  Errors appear below.  All other programs run fine.  I have not changed evo configurations in a long time.  I am running updated 7.04 on an IBM T40.  There was a kernel update the other day, but I have a hard time believing that can affect evolution.  While knowing a cause would be nice, I'd really just like to know how to recover so I can read mail and get my calendar again.  Upgrading to a later Ubuntu version now isn't viable as I am in a production environment and these updates tend to be disruptive.

Thanks,

--jh--

CalDAV Eplugin starting up ...

(evolution-2.10:9390): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:9390): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.10:9390): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:9390): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:9390): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:9390): DEBUG: mailto URL program: evolution
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

---

### Post by JoeHarr4 on 2008-06-21
This appeared to be a corrupted database for my Inbox.  Kill evo and all helper aps.  MOVE the corrupt file and all its attending files elsewhere.  Start evo.  Then, COPY just the email back (this is the big file without extension).  Backup your mail before trying!  Do at your own risk!  Keep your copy!

--jh--

---

