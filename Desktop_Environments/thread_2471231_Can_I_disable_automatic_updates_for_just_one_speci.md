---
title: "Can I disable automatic updates for just one specific Gnome extension?"
date: 2022-01-24
forum: Desktop Environments
---

### Post by Paddy Landau on 2022-01-24
I have a few Gnome extensions installed on my Ubuntu 20.04 system.

There is a specific one, [Hide Top Bar]("https://extensions.gnome.org/extension/545/hide-top-bar/"), great for increasing available screen space, but it breaks every time it's updated.

I have to download and manually install an older version of Hide Top Bar. But, whenever the computer restarts, Gnome automatically updates the extension, thereby breaking it (again).

Here are my three attempts to fix the problem (recommended on the internet):

[HR][/HR]
**Change the name**

[LIST]
[*]Change the UUID in metadata.json, and rename the folder accordingly. Restart Gnome.
[/LIST]
This works at first, but then Gnome uninstalls the extension after restarting the computer. So, no good.

[HR][/HR]
**Enable Gnome's version check**

[LIST]
[*]dconf Editor > /org/gnome/shell/ > disable-extension-version-validation > False
[/LIST]
This works; but it also disables a number of other extensions. Again, no good.

[HR][/HR]
**Set the extension to read-only.**

[LIST]
[*]chmod --recursive go-rwx,u-w ~/.local/share/gnome-shell/extensions/hidetopbar@mathieu.bidon.ca
[/LIST]
This prevents updates to the extension, but with two disadvantages.

[LIST]
[*]Every time I log in, Gnome gives me two messages:
[LIST]
[*]Request to update the extension
[*]An error message because the extension couldn't be auto-updated.
[/LIST]

[*]Gnome sometimes (arbitrarily) disables the extension, and I have to restart Gnome to re-enable it.
[/LIST]
So, it works, but with nagging and arbitrary breakages. I'm using this method at the moment.

[HR][/HR]
So, I'd love to be able to disable auto-updates, but for only the one extension, and without the nagging and arbitrary disabling.

Gnome doesn't have a built-in method. There is a [feature request]("https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/2514"), but the request is already a year old and is unlikely to be implemented any time soon, if at all.

Do you know a good workaround to do disable the auto-update for just the one extension, please?

---

### Post by SeijiSensei on 2022-01-24
If it's installed as an apt package, you could maybe try "apt-mark hold".

```

apt-mark
apt 2.2.4ubuntu0.1 (amd64)
Usage: apt-mark [options] {auto|manual} pkg1 [pkg2 ...]

apt-mark is a simple command line interface for marking packages
as manually or automatically installed. It can also be used to
manipulate the dpkg(1) selection states of packages, and to list
all packages with or without a certain marking.

Most used commands:
  auto - Mark the given packages as automatically installed
  manual - Mark the given packages as manually installed
  minimize-manual - Mark all dependencies of meta packages as automatically installed.
  hold - Mark a package as held back
  unhold - Unset a package set as held back
  showauto - Print the list of automatically installed packages
  showmanual - Print the list of manually installed packages
  showhold - Print the list of packages on hold

See apt-mark(8) for more information about the available commands.
Configuration options and syntax is detailed in apt.conf(5).
Information about how to configure sources can be found in sources.list(5).
Package and version choices can be expressed via apt_preferences(5).
Security details are available in apt-secure(8).

```

---

### Post by Paddy Landau on 2022-01-24
> **SeijiSensei said:**
> If it's installed as an apt package…
This gives me the answer.

It wasn't installed through the repository, but instead through the [Gnome extensions interface]("https://extensions.gnome.org/local/").

I was unaware that you could install them through the repositories (TIL).

I've uninstalled the extension, and reinstalled it using apt. This does the job!

Thank you!

---

