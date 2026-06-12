---
title: "Disable compiz by default for newly created users?"
date: 2009-12-25
forum: Desktop Environments
---

### Post by TwistedLincoln on 2009-12-25
When one is running Ubuntu on a system that supports 3d acceleration, is it possible to stop compiz from being automatically enabled for new users?

I don't want to disable compiz entirely (some users may want to enable it), but don't want to force it on new users either.

I've tried various solutions using the /etc/skel profile, but nothing has worked so far.  I could probably put "metacity --replace" in the /etc/skel profile's session, but then if a user decides to enable compiz it will be reset upon each login unless they change their session info...

The solution found here: [http://ubuntuforums.org/showthread?p=3770282]("http://ubuntuforums.org/showthread?p=3770282") doesn't seem to work in Karmic, as there is no /usr/share/gnome/default.session file to edit.

Can anyone shed some light on this?

---

### Post by TwistedLincoln on 2010-01-19
Can anyone help with this?

---

### Post by TwistedLincoln on 2010-06-04
Any chance anyone can shed some light on this?

---

### Post by TwistedLincoln on 2010-09-12
I finally figured this out.  Place a file in /etc/skel/.gconf/desktop/gnome/applications/window_manager called %gconf.xml with the following code:

> <?xml version="1.0"?>
<gconf>
	<entry name="current" mtime="1264969576" type="string">
		<stringvalue>/usr/bin/metacity</stringvalue>
	</entry>
	<entry name="default" mtime="1216184348" type="string">
		<stringvalue>/usr/bin/metacity</stringvalue>
	</entry>
</gconf>

If you are using an existing user's profile to base your /etc/skel profile on, you'll notice that the stringvalues are set to /usr/bin/compiz.  Just change compiz to metacity, and you're all set.

---

