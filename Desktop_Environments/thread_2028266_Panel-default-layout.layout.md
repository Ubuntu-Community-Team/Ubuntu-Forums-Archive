---
title: "Panel-default-layout.layout"
date: 2012-07-17
forum: Desktop Environments
---

### Post by nadarockyraccoon on 2012-07-17
Hello,
I'm currently attempmting to edit the panel-default-layout.layout for the gnome panel under ubuntu 12.04 using the gnome fallback. I have various reasons for this but the main is that I would like to clear my home directoties hidden content on regular basis without losing custom icons. All was well until I got to the custom launcher and I've been stuck since.

[Object launcher]
object-iid=PanelInternalFactory::Launcher
toplevel-id=top-panel
pack-index=1

With this I get Launcher Location not set Launcher could not be loaded(obviously) and if I attempted to add:

launcher-location=*path_to_app*

I get an erorr saying unknown key 'launcher-location'.I've tried several variations on launcher-location, like it's predecessor launcher_location all with no luck. At this point I'm not even sure that the location is even listed as a key of the launcher object and maybe I'm going about it all wrong. I'm just not sure as things have definately changed and I can't find any documentation to show how.

thanks in advance

---

