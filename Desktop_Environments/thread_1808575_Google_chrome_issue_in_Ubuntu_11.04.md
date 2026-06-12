---
title: "Google chrome issue in Ubuntu 11.04"
date: 2011-07-20
forum: Desktop Environments
---

### Post by Detroit_Bad_Boy on 2011-07-20
I am at my wits end. I have tried and tried to get vicidial to work with google chrome in Ubuntu 11.04. 

Here is the situation:

  I work for a company that requires that I use google chrome. Here is the result of the procedure in Windows 7. They use the vicidial program which I can access as a rep of the company. I input my username and password and press enter. A dropdown icon appears that says "Please choose your campaign state". I click that, then choose the state I am working and viola! It logs me in. 
  When I run this procedure with google chrome in ubuntu 11.04 I am stopped at the part that calls for choosing your campaign state. When I click on that I only get "Please choose your campaign state"
  I can use any softphone so long as the variables are correct to access their system, so that is not ans issue.
  Am I missing something here? Do I need to install any packages to clear up the issue? HELP!!!!!!!!!!!!!!!!

---

### Post by UCSBGauchosRock on 2011-07-20
Hmmm you may have an issue with plugins in that browser. I don't know a whole lot about google chrome mainly because I use Firefox, but I do know it uses it's own integration of Flash.

What I would try to do is install ubuntu's restricted extras via the command

"sudo apt-get install ubuntu-restricted-extras"  (Without the quotes)

If that fails try manually installing java and flash from their respective websites or from Ubuntu Software Center or Synaptic Package Manager.

---

### Post by Detroit_Bad_Boy on 2011-07-21
> **UCSBGauchosRock said:**
> Hmmm you may have an issue with plugins in that browser. I don't know a whole lot about google chrome mainly because I use Firefox, but I do know it uses it's own integration of Flash.

What I would try to do is install ubuntu's restricted extras via the command

"sudo apt-get install ubuntu-restricted-extras"  (Without the quotes)

If that fails try manually installing java and flash from their respective websites or from Ubuntu Software Center or Synaptic Package Manager.


I tried that and something went wrong. After the download/install completed I could not download anything else through a terminal or through the download center. It kept giving me a python error in line 961. So I wiped down the HD and started from scratch.
UPDATE: I found that the microphone works through google voice in gmail so I think the issue may be with an audio driver for the headphones. I am currently using ALSA but I think I may need something different so as to have X-Lite find the audio driver. Still a bit confounding though.

---

### Post by UCSBGauchosRock on 2011-07-21
> **Detroit_Bad_Boy said:**
> I tried that and something went wrong. After the download/install completed I could not download anything else through a terminal or through the download center. It kept giving me a python error in line 961. So I wiped down the HD and started from scratch.
UPDATE: I found that the microphone works through google voice in gmail so I think the issue may be with an audio driver for the headphones. I am currently using ALSA but I think I may need something different so as to have X-Lite find the audio driver. Still a bit confounding though.


It is very well possible that you may have had or have broken/corrupted packages on the system.

It's very odd and I am not certain that the problem lies within the audio driver or it could be a corruption of ubuntu.

To check and fix broken packages run "sudo dpkg --configure -a" If this command does not return anything, you do not have broken packages on your system. If the command does return something, it will automatically fix packages. 

Unfortunately I haven't had run ins with this error yet so I'm sorry if I can't be of too much help.

---

