---
title: "Domain-Wide/Multiple PC Configuration"
date: 2010-06-16
forum: Desktop Environments
---

### Post by pyrotherm on 2010-06-16
Hi all,

I have a pretty simple question, but can't seem to find an answer through my searching.

I know that there has to be a way to configure multiple Ubuntu machines somewhat easily, but how to do this exactly?

If anyone could link me to a network best practices thread or something that explains network administration of multiple Ubuntu clients, I would be extremely grateful.

Cheers,
Pyrotherm

---

### Post by SoFl W on 2010-06-16
Are you looking for multiple users logging on to any computer and having access to their data?
[http://ubuntuforums.org/showthread.php?t=1501558](http://ubuntuforums.org/showthread.php?t=1501558)

Or are you looking for every machine having the same programs/configuration?
For that get a image or hard drive copying utility.

---

### Post by pyrotherm on 2010-06-16
Actually, I'm looking for a way to update config files on multiple machines.

I want to edit the apt sources list file to include my Ubuntu repository that I have setup internally here at work, for all of my workstations.

Basically, I'm looking for some type of equivalent to Group Policy, so that I may make domain-wide changes to system's configurations.

At this point, my best idea is a shell script that copies my modified config file over the one currently on the workstations, but this will require a physical trip to each workstation with a flash drive, and I consider this a last-resort option.

---

