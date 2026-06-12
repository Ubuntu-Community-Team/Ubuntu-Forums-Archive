---
title: "Battlefield 1942 doesnt start"
date: 2005-01-09
forum: Gaming &amp; Leisure
---

### Post by largo on 2005-01-09
Hi
I tried to install battlefiel over cedega 4.2. the installation went well. I also installed the patch for Version 1.6.19 which was no problem with cedega. After replacing some files (NoCD patch)I tried to start the game with cedega. For a couple of seconds, the screen went black. after that it went back to my desktop, shown in a very low resolution and I got an error message in the console, where i startet battlefield:

```

found key:OBJECTIVEMODE 
found key:TOOLTIP_COMMANDORAFT_HEADING
found key:TOOLTIP_COMMANDORAFT
found key:TOOLTIP_ANTI_TANK_GUN_HEADING
found key:TOOLTIP_ANTI_TANK_GUN
found key:TOOLTIP_KETTENKRAD_HEADING
found key:TOOLTIP_KETTENKRAD
found key:OBJECTIVEMODE
found key:VICTORY found key:DEFEAT
found key:Factory found key:AXIS_DESTROYED_OBJECTIVE1
found key:ALLIES_DESTROYED_OBJECTIVE1
found key:CREDITS_FREE_CONTENT
found key:CREDITS_1_6_FORWARD
mmtime pid=24610 tid=24622
X Error of failed request: BadValue (integer parameter out of range for operati on)
 Major opcode of failed request: 145 (ATIFGLRXDRI)
 Minor opcode of failed request: 1 ()
 Value in failed request: 0x76
 Serial number of failed request: 3823
 Current serial number in output stream: 3823

```


there are way more found key lines before that, but i assume that is a good ting.

Can anyone tell me whats going wrong?

---

### Post by justin whitaker on 2005-01-14
[QUOTE=largo]Hi
I tried to install battlefiel over cedega 4.2. the installation went well. I also installed the patch for Version 1.6.19 which was no problem with cedega. After replacing some files (NoCD patch)I tried to start the game with cedega. For a couple of seconds, the screen went black. after that it went back to my desktop, shown in a very low resolution and I got an error message in the console, where i startet battlefield:

```

found key:OBJECTIVEMODE 
found key:TOOLTIP_COMMANDORAFT_HEADING
found key:TOOLTIP_COMMANDORAFT
found key:TOOLTIP_ANTI_TANK_GUN_HEADING
found key:TOOLTIP_ANTI_TANK_GUN
found key:TOOLTIP_KETTENKRAD_HEADING
found key:TOOLTIP_KETTENKRAD
found key:OBJECTIVEMODE
found key:VICTORY found key:DEFEAT
found key:Factory found key:AXIS_DESTROYED_OBJECTIVE1
found key:ALLIES_DESTROYED_OBJECTIVE1
found key:CREDITS_FREE_CONTENT
found key:CREDITS_1_6_FORWARD
mmtime pid=24610 tid=24622
X Error of failed request: BadValue (integer parameter out of range for operati on)
 Major opcode of failed request: 145 (ATIFGLRXDRI)
 Minor opcode of failed request: 1 ()
 Value in failed request: 0x76
 Serial number of failed request: 3823
 Current serial number in output stream: 3823

```


there are way more found key lines before that, but i assume that is a good ting.

Can anyone tell me whats going wrong?[/QUOTE]


Hey largo,

The latest release notes for Cedega have some ATI workarounds for  BF1942. Also, try reinstalling it without the no-cd, sicne from your output, it looks like it is throwing serial errors.

---

### Post by thetron on 2005-02-11
Has anyone sucessfully tested Desert Combat and DC_final?

---

