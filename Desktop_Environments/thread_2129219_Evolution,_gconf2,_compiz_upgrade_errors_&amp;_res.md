---
title: "Evolution, gconf2, compiz upgrade errors &amp; resultant SERIOUS dysfunctions"
date: 2013-03-25
forum: Desktop Environments
---

### Post by questant on 2013-03-25
Where does this (display) problem (bug) need to be posted in order to be addressed?
Two problems:
1.  See post (Link below contains visuals) on Evolution and GEdit video display errors. The result is Evolution is unusable and GEdit is hampered.  Is it a video driver problem?  Is it a Gnome problem?  Is it an Evoloution and/or GEdit problem?  Is it a Novell problem?  Is it a more endemic Ubuntu or Debian problem (It seems to show up in Fedora and others)?

[http://ubuntuforums.org/showthread.php?t=2127370&highlight=evolution+gedit](http://ubuntuforums.org/showthread.php?t=2127370&highlight=evolution+gedit)

2. Update and Upgrade problem: It may or may not be related to the first problem.

	Processing triggers for gconf2 ...
	WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/view/show-priority-column)
	WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/do_notification)

The warning list also has lines for restore-size, restore-position, ask-delete-category, show-due-column, auto-purge, hide-done, hl-due, hl-today, and hl-indays.

In Debian and its stream of release flavors, this second problem appears to have the nine lives of a cat. Apparently, it's been around since 2010. There are at least four separate bug number assignments (maybe more ... I stopped looking) but no solutions.

The video display issues with Evolution and Gnome may have nothing to do with one another, but I doubt it.  The "Processing triggers" may be a separate issue entirely but I've come to wonder.

From /var/log.apt/term.log the error appears right after logged modifications of
	compiz-plugins-main
	compizconfig-settings-manager
	Any install or removal of Evolution

What is most important is how these problems can be addressed so the sofware that depends on their solution can be used.  If someone needs Evolution in a production environment (and many of us do), they're SOL.
We use standard Ubuntu 12.04.1? LTS installs (The LTS part is very important) with Mate and Cinnamon desktops added. We don't use Mint. I do use Unity and Gnome3 periodically but I tweak my environments for work flow and find Unity and Gnome3 more resistant and opaque to that process.
Any assistance would be appreciated.

---

