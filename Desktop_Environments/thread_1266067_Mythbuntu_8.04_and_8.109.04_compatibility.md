---
title: "Mythbuntu 8.04 and 8.10/9.04 compatibility"
date: 2009-09-14
forum: Desktop Environments
---

### Post by Tux+ on 2009-09-14
I have mythtv running on 8.04 using the Mythbuntu control panel to set it up. It is running fine.

Recently I have got a new machine and want to move the existing 8.04 to a headless server and the new machine as a desktop computer. I ran into stability problems trying to run 8.10 and 9.04 and could not afford the time to troubleshoot it but wanted the new releases because it worked with the Hauppauge TD-500 (see my thread [Mythbuntu 8.04 Nova TD 500 compatibility]("http://ubuntuforums.org/showthread.php?t=1084576")).

I want the new computer to be on the latest release, 9.04 but it should not be on 24/7 because thats what the 8.04 computer is for. With this in mind, how compatibile is it using a 8.04 as the master backend and a 9.04 as a slave with a capture card?

---

### Post by Tux+ on 2009-09-15
bump

---

### Post by Tux+ on 2009-09-17
I decided to take the jump and tried it out myself.

Everything went fine till I wanted to use the tuner in the backend slave computer. As far as I was aware the slave could see all the master backend like recordings to watching live TV with the tuner card in the master backend.

According to Mythweb, the encoders on the slave backend are registed but display currently not connected (or something to that effect) rendering the slave more or less useless for my purpose.

Also doing a mythfillbackend did not get the TV schedule data for the slave encoders (I was using EIT for slave and radioTimes xmltv for master).

I would try 9.04 as master and 8.04 as slave but it does not fit my current set up.

---

