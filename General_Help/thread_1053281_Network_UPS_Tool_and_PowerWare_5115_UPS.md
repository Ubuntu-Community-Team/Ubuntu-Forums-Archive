---
title: "Network UPS Tool and PowerWare 5115 UPS"
date: 2009-01-28
forum: General Help
---

### Post by digitrance on 2009-01-28
Hi there,

I am trying to set up a PowerWare 5115 UPS on a Dell PowerEdge 6650 server running Ubuntu 8.04 LTS Server Edition. In brief, I have followed the following steps:

Installed NUT using apt-get
Looked up PowerWare 5115 on NUT's website - should use bcmxcp driver
Configured NUT

The part I'm getting stuck on now is starting the service. Nut starts fine using the command:

> 
$ sudo /etc/init.d/nut start


But then when I try to start up the bcmxcp driver I get:

> 
$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.2.1-
Network UPS Tools - BCMXCP UPS driver 0.13 (2.2.1-)

Warning: This is an experimental driver.
Some features may not function correctly.

Attempting to autodect baudrate
Can't connect to the UPS on port /dev/ttyS0!

Driver failed to start (exit status=1)


The serial port seems to be fine however:

> 
$ setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test


And the UPS was working properly on this same server running Windows Small Business Server 2003 just days ago. Any ideas as to what I can try?

---

### Post by MysticGold04 on 2009-01-28
Maybe adjust the baud rate down to 9600 on the port if there is a way to do that... Windows usually defaults to 9600 on serial ports.

---

### Post by digitrance on 2009-01-28
MysticGold04,

Thanks for the response.

I originally had the baud rate manually configured to 9600. And according to bcmxcp's man page it also defaults to 9600, but then goes into "hunting mode" if that's not it. So I don't believe that's the problem.

---

### Post by MysticGold04 on 2009-01-28
Well, it was a shot... by chance do you know the specs on the UPS as far as what baud rate it wants to be connected at?  If there's a way to configure bcmxcp manually, maybe try hard coding the rate.

---

### Post by digitrance on 2009-01-29
I looked through the User's Guide, but no mention of baud rate. Manually configuring the driver for 9600 gets the following results:

> 
$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.2.1-
Network UPS Tools - BCMXCP UPS driver 0.13 (2.2.1-)

Warning: This is an experimental driver.
Some features may not function correctly.

No response from UPS on /dev/ttyS0 with baudrate 9600
Attempting to autodect baudrate
Can't connect to the UPS on port /dev/ttyS0!

Driver failed to start (exit status=1)


The man page for bcmxcp reads:

> 
BCMXCP(8)                   Network UPS Tools (NUT)                  BCMXCP(8)

NAME
       bcmxcp - Driver for UPS’es supporting the BCM/XCP protocol

NOTE
       This  man  page  only  documents  the hardware&#8208;specific features of the
       bcmxcp driver.  For information about  the  core  driver,  see  nutups&#8208;
       drv(8).

SUPPORTED HARDWARE
       This  driver  should  recognize  all BCM/XCP-compatible UPS’es.  It has
       been developed and tested on Powerware PW5115 and PW9120 hardware.

EXTRA ARGUMENTS
       This  driver  supports  the  following   optional   settings   in   the
       ups.conf(5).

       shutdown_delay=delay
              The number of seconds that the UPS should wait between receiving
              the shutdown command (OB LB) and actually shutting off.

       baud_rate=rate
              Communication speed for the UPS. If this is set to 9600, it  try
              to connect to the UPS on 9600bps. If it fails to communicate, it
              go into baudhunting.  It start at 1200 and up to  19200.  If  it
              succeed  it  tell you the speed it connect with. If not included
              in the config it default’s to baudhunting.

DEFAULT VALUES FOR THE EXTRA ARGUMENTS
       shutdown_delay = 180

       baud_rate = none

INSTANT COMMANDS
       This driver supports the following Instant Commands:

       shutdown.return
              Turn off the load and return when power is back.

       shutdown.stayoff
              Turn off the load and remain off.

       test.battery.start
              Start a battery test.

TODO LIST
       Report UPS alarm status
              BCM/XCP supports reporting a wide range of UPS alarm conditions.

       Report UPS statistics informations
              BCM/XCP supports reporting of UPS statistics data.

BUGS
       None known.

AUTHOR
       Tore Ørpetveit <tore AT orpetveit DOT net>

SEE ALSO
   The core driver:
       nutupsdrv(8)

   Internet resources:
       The NUT (Network UPS Tools) home page: [http://www.networkupstools.org/](http://www.networkupstools.org/)

                                Thu Sep 29 2005                      BCMXCP(8)
 Manual page bcmxcp(8) line 55/85 (END)


---

### Post by digitrance on 2009-01-29
Maybe I should mention too that this is a PowerWare 5115 **RM**. It's not the standard one, but a rack-mounted UPS. Just noticed today that they have a PowerWare 5115 that isn't rack-mountable. I don't know if that makes a difference or not, though.

---

### Post by AMD64_N_Linux on 2009-03-17
First of all, I am not sure that there is a difference between the Rackmount model and mine.

Saying that, I have the PW_5115 750 myself. A GREAT UPS.

I had forgotten how to set it up, because until 2 days ago I was running Ubuntu 7.04.

I just installed Mint Linux, based on Ubuntu Intrepid.

These instructions worked perfectly for me.

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

I did not use the first section "GNOME Power Manager and HAL", see the warning.

But from the ups.conf section on down, worked perfectly.

Now to find a GUI monitoring program. I have been using KNut for several years, but am intriged by a OSD model I read about yesturday morning.

Good luck and enjoy.

---

