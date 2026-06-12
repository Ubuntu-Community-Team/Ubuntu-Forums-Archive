---
title: "crash while zoning"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by MiniNightMana on 2007-09-03
Afternoon guys WoW is up and running. I sometimes crash though when zoning

its runs this line over and over
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)

and just never completes the load process to the zone and stays on the loading screen

Im running at about 35 fps. No other problems in game at all

Any ideas ?

---

### Post by MiniNightMana on 2007-09-04
SET gxApi "opengl"


Seems I was able to fix it by adding this to my config file, however I am now lagging for the first time in WoW history.
Any suggestions ?

---

