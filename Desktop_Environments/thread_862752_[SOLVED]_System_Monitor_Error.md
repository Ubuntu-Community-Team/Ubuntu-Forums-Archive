---
title: "[SOLVED] System Monitor Error"
date: 2008-07-17
forum: Desktop Environments
---

### Post by socceroos on 2008-07-17
Hello Everyone, I've installed KDE 4.1 RC 1 and am having problems with the System Monitor giving me the following error:

"Connection to localhost has been lost"

It still shows all the current processes, but when trying to use the 'System Load' tab it shows nothing but blank boxes.

Here is the errors I get when I run 'ksysguard' from the terminal:

ksysguard(28127) Workspace::readProperties: Selected Sheets =  ("ProcessTable.sgrd", "SystemLoad.sgrd", "Sheet 3.sgrd")
ksysguard(28127) WorkSheet::replaceDisplay: Found process controller
ksysguard(28127) ProcessController::addSensor: Number of Actions:  15
ksysguard(28127) KSGRD::SensorShellAgent::daemonError: failed to run "ksysguardd"
ksysguard(28127) KSGRD::SensorShellAgent::daemonError: error  "Could not run daemon program 'ksysguardd'."
ksysguard(28127) KSGRD::SensorShellAgent::daemonError: Error recieved  0

---

### Post by socceroos on 2008-07-17
SOLVED:

sudo apt-get install ksysguardd-kde4 fixed the problem. This is a bit odd, it should be a dependency...

---

