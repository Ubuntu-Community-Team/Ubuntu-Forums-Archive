---
title: "gpilotd calendar conduit not called"
date: 2005-12-09
forum: Desktop Environments
---

### Post by brj on 2005-12-09
hi all,

the conduits for calendar and addresses are not called when i sync my palm
although these conduits are listed in my conduits file:

[General]
conduits=e_address_conduit e_calendar_conduit e_todo_conduit gpmemo1 

[e_address_conduit]
sync_type=copy_from_pilot
first_sync_type=copy_from_pilot

[e_calendar_conduit]
sync_type=copy_from_pilot
first_sync_type=copy_from_pilot

[e_todo_conduit]
sync_type=copy_from_pilot

[gpmemo1]
sync_type=copy_from_pilot


i can see these conduits in the console when i sync, but no data is transferred from palm to evolution.
setting the sync_type does not help.

gpilotd-Message: setting PILOTRATE=57600
gpilotd-Message: Docking-Station PalmUSB hat 0 Ereignisse
gpilotd-Message: Instantiating 4 conduits...
eaddrconduit-Message: in address's conduit_get_gpilot_conduit

ecalconduit-Message: in calendar's conduit_get_gpilot_conduit
...


jakob

---

### Post by brj on 2005-12-17
the following log shows the output of a sync with only address- and calendar-conduit enabled (both copy from palm):

gpilotd-Message: Using net TRUE
gpilotd-Message: setting PILOTRATE=115200

(gpilotd:14906): gpilotd-WARNING **: Es kann keine Verbindung zu Pilot hergestellt werden.
gpilotd-Message: setting PILOTRATE=115200
gpilotd-Message: Docking-Station PalmUSB hat 0 Ereignisse
gpilotd-Message: Instantiating 2 conduits...
ecalconduit-Message: in calendar's conduit_get_gpilot_conduit

eaddrconduit-Message: in address's conduit_get_gpilot_conduit

gpilotd-Message: Instantiated 0 backup conduits, 0 file conduits, 2 other conduits
gpilotd-Message: HotSync-Knopf gedrückt, Pilot wird synchronisiert
gpilotd-Message: Pilot-Kennung ist 17403, Name ist MyPilot, Besitzer ist Jakob Br\xe4uchi
gpilotd-Message: Pilot has 0 entries in restore queue
gpilotd-Message: Pilot has 0 entries in conduit queue
gpilotd-Message: Synchronisation beendet
gpilotd-Message: setting PILOTRATE=115200

(gpilotd:14906): gpilotd-WARNING **: pi_accept_to: Die Wartezeit für die Verbindung ist abgelaufen

(gpilotd:14906): gpilotd-WARNING **: pi_accept_to: timeout was 40 secs
gpilotd-Message: Beenden (SIGINT empfangen)

none of these conduits seems to work. memo- and todo-conduits are ok.


jakob

---

### Post by brj on 2006-03-12
hi all,

i finally could solve this problem that also affected jpilot.
after resetting the palm all conduits work fine :) 

jakob

---

