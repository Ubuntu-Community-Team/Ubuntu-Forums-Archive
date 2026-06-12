---
title: "[SOLVED] [SOLVED] Planeshift problem... :S"
date: 2008-11-19
forum: Gaming &amp; Leisure
---

### Post by Juggercat on 2008-11-19
Hi everyone. ok, i have the following problem.. When i try to log in to planeshift the game immediatly crashes... apart from having the problem that whenever i would click teh screen it would go black, and i would have to click back to get it right... Can anyone help me? Could this maybe be related to it being 64 instead of 32... cos im not sure.. im a noob lol :P
Much thx in advance..

and here i leave what the console shows...

DEBUG: Sound System Software Renderer Initializing...
ATTENTION: default value of option force_s3tc_enable overridden by environment.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

planeshift.application.client:
  PlaneShift Steel Blue (0.4.01)
  This game uses Crystal Space Engine created by Jorrit and others
  1.4.0 [Unix-x86-GCC]
Thu Nov 20 01:38:23 2008, LOG_ANY flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_WEATHER flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SPAWN flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CELPERSIST flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_PAWS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_GROUP flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CHEAT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_LINMOVE flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SPELLS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_NEWCHAR flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SUPERCLIENT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_EXCHANGES flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_ADMIN flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_STARTUP flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CHARACTER flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CONNECTIONS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CHAT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_NET flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_LOAD flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_NPC flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_TRADE flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SOUND flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_COMBAT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SKILLXP flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_QUESTS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_SCRIPT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_MARRIAGE flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_MESSAGES flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_CACHE flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_PETS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_USER flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_LOOT flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_DUELS flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, LOG_TRIBES flag deactivated with no filter.
Thu Nov 20 01:38:23 2008, All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.
Using fontsize 16 for resolution 1024x768
WARNING! Object 'spikes_05' is not closed!
WARNING! Object 'spikes_03' is not closed!
WARNING! Object '_s_walls_01' is not closed!
WARNING! Object '_s_sigil_01' is not closed!
WARNING! Object '_s_sigil_05' is not closed!
WARNING! Object '_s_bridge_01' is not closed!
...
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
Aborted

---

### Post by Juggercat on 2008-11-19
Ok, i solved the problem of crashing by following what was said here... 

[http://hydlaa.com/smf/index.php?topic=32288.msg371380#msg371380](http://hydlaa.com/smf/index.php?topic=32288.msg371380#msg371380)
i left it like this:

 <rule description="Mesa R200 DRI: Disable texture compression">
        <conditions fulfill="all">
          <regexp string="renderer" pattern="^Mesa DRI R200" />
          <regexp string="glversion" pattern="Mesa 7\.0\.." />
        </conditions>
      <applicable>
        <usecfg>disableTC</usecfg>
      </applicable>
    </rule>

    <!--
      * 2006-11-24: AFP support in Intel DRI (at least in Mesa 6.5.1) is 
                    broken.
      * 2008-05-02: Still broken as of Mesa 7.0.3.
      -->
    <rule description="Intel DRI: Disable ARB_fragment_program">
      <conditions fulfill="all">
        <regexp string="renderer" pattern="Mesa.*Intel" />
        <conditions fulfill="one">
          <regexp string="glversion" pattern="Mesa 7\.0\.." />
          <regexp string="glversion" pattern="Mesa 7\.0\.." />
        </conditions>
      </conditions>
      <applicable>
        <usecfg>noafp</usecfg>
      </applicable>
    </rule>

changing teh version to 7\.0\

but... i still have the problem of the screen going black whenever i click... and going back to normal after a second click.. and alternating so forever.. >.>

---

### Post by Juggercat on 2008-11-19
ok, solved this problem too.

Ran sudo ./pssetup

if not it will not save the changes done to the setup.. due to some permission prob...

changed it to fullscreen...

and works...

hope this helps someone..

bye.

now lets see if the game works... lol

---

### Post by Vadi on 2008-11-20
Glad you got it. Click on 'Thread Tools' and 'Mark thread as solved' ;)

---

### Post by Vadi on 2008-11-20
doublepost

---

