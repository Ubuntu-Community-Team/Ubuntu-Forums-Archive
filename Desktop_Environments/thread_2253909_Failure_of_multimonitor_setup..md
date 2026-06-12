---
title: "Failure of multimonitor setup."
date: 2014-11-23
forum: Desktop Environments
---

### Post by odror on 2014-11-23
OS: Ubuntu 14.10
Video: Nvidia gtx 660 with latest PPA drivers.

I have a 4 monitors setup, which is correctly indicated in ~/.config/monitors.xml
as well as setup in xrandr script in /usr/share/lightdm/lightdm.conf/90-nvidia.conf
> [SeatDefaults]
# Force using traditional X
type=xlocal
display-setup-script=MONITOR-SCRIPT.sh


MONITOR-SCRIPT.sh :> xrandr -display :0 --output DVI-D-0 --mode 2560x1440 --pos 6400x0 --rotate normal --output HDMI-0 --mode 1920x1080 --pos 8960x0 --rotate normal --output DVI-I-1 --mode 2560x1440 --pos 0x0 --rotate normal --output DVI-I-0 --off --output DP-1 --mode 3840x2160 --pos 2560x0 --rotate normal --output DP-0 --of

Each time that I login through lightdm a different monitor setup configuration is used. My setup is being ignored. Also many time on wakeup the monitors rearrange.
How can I force the monitors configueration to be fixed and not changed. things got really worse after I replace one of my monitors with a 4k display.

---

