---
title: "install exe files in virtual box"
date: 2011-08-15
forum: Desktop Environments
---

### Post by fidelandche on 2011-08-15
Hi all,

This is the problem I am facing, I am  trying to install a exe file in virtual box which is running XP on 11.04, I can download the file and install it but I then get a dialogue box stating there is an error, so when I search for the file all I get is unable to find file it might have been changed or removed. When I check I find the programme has been installed but for some reason will not work. The programme is to upload data from my electrical usage meter, when running vista as a dual boot it worked fine, so any ideas would be great.

Cheers

Andy

---

### Post by varunendra on 2011-08-15
> **fidelandche said:**
> Hi all,

This is the problem I am facing, I am  trying to install a exe file in virtual box which is running XP on 11.04, I can download the file and install it but I then get a dialogue box stating there is an error, so when I search for the file all I get is unable to find file it might have been changed or removed. When I check I find the programme has been installed but for some reason will not work. The programme is to upload data from my electrical usage meter, when running vista as a dual boot it worked fine, so any ideas would be great.

Cheers

Andy
Once inside a virtual machine, a program/file has nothing to do with the external (host) operating system, be it Vista or Ubuntu or anything else unless it is network dependent (even in that case, only the network-communication dependent part may get affected). It has everything to do with only the guest OS which is handling it.

What I understand from your description is that the file is used to install the application, then itself gets disappeared. If it is happening after finishing the setup, it may be normal and intentional behaviour of that program. But if it is deleted before the setup is finished, either the installer is buggy or you may have a virus in your XP VM. Check it for the same using some reliable antivirus for windows.

Besides, has the installer file itself come from a trusted source?

---

### Post by fidelandche on 2011-08-15
The installer has come a good source, it has come from the electricity company's website and I have used it before when I was dual booting.

---

### Post by Toz on 2011-08-15
> **fidelandche said:**
> but I then get a dialogue box stating there is an error
And the error is.....?

---

### Post by fidelandche on 2011-08-15
Sorry about that, this is the error message I get

---

### Post by Toz on 2011-08-15
What information does that log file contain?

---

### Post by fidelandche on 2011-08-15
> **Toz said:**
> What information does that log file contain?
 
And this is what the log file contains,
 
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem
Traceback (most recent call last):
  File "uientry.py", line 1, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\ui.pyo", line 22, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\upload.pyo", line 20, in <module>
  File "zipextimporter.pyo", line 82, in load_module
  File "client\device.pyo", line 21, in <module>
  File "ctypes\__init__.pyo", line 395, in LoadLibrary
  File "ctypes\__init__.pyo", line 312, in __init__
WindowsError: [Error 22] This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem

---

### Post by fidelandche on 2011-08-15
I had a look in the device manager and there is nothing wrong there, I also checked the error code with Microsoft and the site said look in the device manager as something might not be configured.

---

### Post by varunendra on 2011-08-15
> **fidelandche said:**
> Sorry about that, this is the error message I get
And what are those two shield type icons in the system tray? The yellow one should be normal MS security alert, but I'm suspicious about the red one. When you hover the pointer over it, what does the balloon tip say?

AVG is one of the worst AVs I have tried. Try Avira instead (if your XP is still intact at all..!!).

It maybe another reason for the error, but the red shield icon makes me more suspicious about a virus infection.

If you took a snapshot when the installation was fresh, try returning to it.

---

### Post by fidelandche on 2011-08-15
> **varunendra said:**
> And what are those two shield type icons in the system tray? The yellow one should be normal MS security alert, but I'm suspicious about the red one. When you hover the pointer over it, what does the balloon tip say?
 
AVG is one of the worst AVs I have tried. Try Avira instead (if your XP is still intact at all..!!).
 
It maybe another reason for the error, but the red shield icon makes me more suspicious about a virus infection.
 
If you took a snapshot when the installation was fresh, try returning to it.
 
 
The yellow shield is for an update of IE which I do not want because access to my work emails and certain applications that I can run from home only work in IE7, so I am not updating IE and the red one is stating that AVG is turned off

---

### Post by fidelandche on 2011-08-15
now changed the antivirus to Avira as AVG was causing problems and the system is clean...no virus and the red shield has gone as Avira is running instead of AVG.

---

### Post by varunendra on 2011-08-15
Does this software depend upon some specific hardware/sensors? If so, are they connected to the VM and detected by it? This seems to be the most probable explanation to the error code. For example, lmsensors doesn't work in my natty VM because a VM has no heat sensors in it.


**_EDIT_:**
As a side note, if you wish to use avira for XP, go into advance configuration mode, and set heuristics to 'high' in both 'scan' and 'guard' options. Then goto General > Security and make sure all the check boxes are checked (advance process protection is disabled by default). High heuristics will obviously increase the possibility of 'false alerts', but offers better protection. Advance process protection will make sure the security engine gets loaded and running as early as possible during boot up.

Needless to say, this will affect the performance, but that's the cost of running windows :). Besides, I haven't noticed any difference on my physical machine. On my VMs, I don't install such bloatwares at all. Instead I use snapshots. Should anything go wrong, just return to a working one ;)

---

### Post by fidelandche on 2011-08-15
> **varunendra said:**
> Does this software depend upon some specific hardware/sensors? If so, are they connected to the VM and detected by it? This seems to be the most probable explanation to the error code. For example, lmsensors doesn't work in my natty VM because a VM has no heat sensors in it.

The only thing it needs is for the electricity meter to be connected via a USB port to upload the information on it, I have tried with the meter connected before downloading the file and I still get the same error message once installed.

---

### Post by varunendra on 2011-08-15
> **fidelandche said:**
> The only thing it needs is for the electricity meter to be connected via a USB port to upload the information on it, I have tried with the meter connected before downloading the file and I still get the same error message once installed.
Maybe I'm not understanding it correctly, but you mean the meter uploads its data to the software in XP, right? So when you connected the meter to the VM via USB, did xp detect a usb device connected and configured it?

Since the meter is the data source with which the software has to work, it may be looking for it to configure during installation, in absence of which the installation gets failed. Just a guess as I've no idea how it works.

---

### Post by fidelandche on 2011-08-15
> **varunendra said:**
> Maybe I'm not understanding it correctly, but you mean the meter uploads its data to the software in XP, right? So when you connected the meter to the VM via USB, did xp detect a usb device connected and configured it?

Since the meter is the data source with which the software has to work, it may be looking for it to configure during installation, in absence of which the installation gets failed. Just a guess as I've no idea how it works.

Yep, the meter uploads the data via this uploader, which at the moment only works with windows or mac.

When connected the VM does detect the meter and also installs the driver for it, I have tried to download the file with the meter connected but I still get the same error message.

---

### Post by varunendra on 2011-08-15
Do you have access to another (physical) windows machine on which the same downloaded installer can be tested?

I now slightly doubt if it can work with virtualized hardware, although there seems no reason if the usb meter is detected and installed by the system. If possible, you should confirm this with the software providers.

---

### Post by fidelandche on 2011-08-15
> **varunendra said:**
> Do you have access to another (physical) windows machine on which the same downloaded installer can be tested?

I now slightly doubt if it can work with virtualized hardware, although there seems no reason if the usb meter is detected and installed by the system. If possible, you should confirm this with the software providers.

Nope no access to another windows machine, before I used a VM I was dual booting with Vista and the installer worked then.

I will try to speak to the providers and see what they say.

Cheers

---

