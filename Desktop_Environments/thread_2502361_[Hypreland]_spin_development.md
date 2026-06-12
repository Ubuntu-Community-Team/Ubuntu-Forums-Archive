---
title: "[Hypreland] spin development"
date: 2024-11-11
forum: Desktop Environments
---

### Post by tdk-bob on 2024-11-11
Hi I hope I'm doing this right as I got told to come here from the stack overflow, If not please let me know. 

I recently upgraded to the new image and saw that hyprland as well as several of nwg-piotr's applications where avaliable in the repo. I used those to build a nearly complete nwg environment and session. And they seem to be working well. 

My question is would there be interest in working on a complete community supported edition/spin /flavor of ubuntu. Similar to the sway variant.

I'm running on older hardware so I can not take point on the building of it but I can still use my set-up to test configurations. 

Hope to hear something back.
Nick

---

### Post by grahammechanical on 2024-11-12
> I recently upgraded to the new image and saw that hyprland as well as  several of nwg-piotr's applications where avaliable in the repo

I saw the above and wondered if you was on the right forum. Then I found this:

[https://wiki.hyprland.org/Getting-Started/Installation/#packages](https://wiki.hyprland.org/Getting-Started/Installation/#packages)

Under the heading for Ubuntu it says:

> Hyprland made it into the Ubuntu 24.10 Oracular Oriole universe repo and can be installed with

```
sudo add-apt-repository universe && sudo apt-get update && sudo apt-get install -y hyprland
```

Hyprland and Sway are Wayland compositors and tiling window managers. Is the intention to develop either of these into a desktop environment? What is your position on Canonical's use of Snap packaging? Will an experimenter have to remove snapd?

Regards

---

### Post by tdk-bob on 2024-11-23
Yes sir,  I'm aware the packages are in the repos, thats what sparked this idea. Granted they are slightly behind current release last I checked. I'm just wondering if people would want this packaged as a dedicated distro (Ala kububtu/lubuntu/etc).

As for my position on snap, I haven't used it enough to really say. I've been primarily using apt and flatpak. Not out of preference persay so much as they where the package formats and managers I was first exposed to. If I where shown an interested party that would rather use the one or the other then great we could look into that mode of distribution. But that's not really what I'm interested in. 

As I said I'm looking at this from a full iso standpoint so packaging together things like hypercursor, azote, the nwg apps, fuzzle, and all the other apps needed to make a fully functional system. I'm not hard married to any of these picks they are just the ones I'm running so I know they work together well. 

As for removing snapD I'm honestly ambivalent, I haven't removed it ... I just built over top the sway image as I said and I'm pretty sure that ships with snapD so &#129335;  meh  (more sounds of ambivalence).

And the thing with sway is it already has a maintainer for a ubuntu distribution. While I would like to colaberate with that team to leverage some of their knowledge of integrating wayland compositors into ubuntu. I feel this project would be better suited to a dedicated team, not as a secondary commitment on top of their existing workload. But by all means if some of their members care to take this on as well I will not exclude them. Many hands make light work after all.

Hope that clearifys things amd sorry for the late reply I'm having power outages so I can't get online somedays.

---

