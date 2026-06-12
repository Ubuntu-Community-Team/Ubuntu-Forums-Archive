---
title: "Where are the screensaver and power management scripts?"
date: 2009-04-25
forum: General Help
---

### Post by Paddy Landau on 2009-04-25
I've discovered the locations of the scripts that control what happens on the following power events:

[LIST]
[*]Power-on: /etc/acpi/start.d
[*]Plug into AC: /etc/acpi/ac.d
[*]Unplug AC: /etc/acpi/battery.d
[*]Suspend, resume, hibernate & thaw: /usr/lib/pm-utils/sleep.d
[/LIST]
But...

Where do I find the scripts that control what happens on the power management events screensaver start, screensaver end, put display to sleep, and turn on display?

I've searched these forums and don't know where else to look.

I use both Hardy 8.04 and Intrepid 8.10.

---

### Post by joeyknuccione on 2009-04-25
> **Paddy Landau said:**
> I've discovered the locations of the scripts that control what happens on the following power events:

[LIST]
[*]Power-on: /etc/acpi/start.d
[*]Plug into AC: /etc/acpi/ac.d
[*]Unplug AC: /etc/acpi/battery.d
[*]Suspend, resume, hibernate & thaw: /usr/lib/pm-utils/sleep.d
[/LIST]
But...

Where do I find the scripts that control what happens on the power management events screensaver start, screensaver end, put display to sleep, and turn on display?

I've searched these forums and don't know where else to look.

I use both Hardy 8.04 and Intrepid 8.10.
Maybe do:

Synaptics Package Manager

Search for screensaver, or whatever particular item

Then select properties

Then select Installed Files to search for locations.

---

### Post by Paddy Landau on 2009-04-26
> **joeyknuccione said:**
> Synaptics Package Manager ... select Installed Files to search for locations.
Thanks for the idea. I found what I though were some possibilities, such as /etc/pm and /etc/apm, but unfortunately they turned out to be dead leads.

Still searching...

Were would such things be documented? If I knew, I could mosey around there.

---

