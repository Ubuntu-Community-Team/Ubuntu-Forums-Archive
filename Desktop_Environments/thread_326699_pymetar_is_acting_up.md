---
title: "pymetar is acting up"
date: 2006-12-28
forum: Desktop Environments
---

### Post by p2cd3 on 2006-12-28
I have conky working & looking good.  I am using edgy.  I added pymetar & set my weather station up, it was working & showing my weather, now the terminal screen shows this:

jack@jack-desktop:~$ conky
Conky: forked to background, pid is 8488
jack@jack-desktop:~$
Traceback (most recent call last):
  File "/usr/bin/pymetar", line 32, in ?
    pr=rp.ParseReport(rep)
  File "/usr/lib/python2.4/site-packages/pymetar.py", line 821, in ParseReport
    local,rt=data.split("/")
ValueError: too many values to unpack
Conky: desktop window (100000f) is subwindow of root window (a3)
Conky: window type - override
Conky: drawing to created window (2800002)
Conky: drawing to double buffer

This is my conkyrc:

# conky configuration

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 10

# border width
border_width 2

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Minimum size of text area
minimum_size 5 5
maximum_width 680

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(


# Possible variables to be used:
#
#      Variable         Arguments                  Description

#       addr              (interface)   IP address for an interface
#       acpiacadapter                   ACPI ac adapter state.                  
#       acpifan                         ACPI fan state                          
#       acpitemp                        ACPI temperature.                       
#       adt746xcpu                      CPU temperature from therm_adt746x      
#       adt746xfan                      Fan speed from therm_adt746x            
#       alignr            (num)         Right-justify text, with space of N
#       alignc                          Align text to centre
#       battery           (num)         Remaining capasity in ACPI or APM       
#                                       battery. ACPI battery number can be     
#                                       given as argument (default is BAT0).    
#       buffers                         Amount of memory buffered               
#       cached                          Amount of memory cached                 
#       color             (color)       Change drawing color to color           
#       cpu                             CPU usage in percents                   
#       cpubar            (height)      Bar that shows CPU usage, height is     
#                                       bar's height in pixels
#       cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
#                                       CPU usage graph, with optional colours in hex,
#                                       minus the #.
#       downspeed         net           Download speed in kilobytes             
#       downspeedf        net           Download speed in kilobytes with one    
#                                       decimal                                 
#       downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
#                                       Download speed graph, colours defined in
#                                       hex, minus the #.
#       exec              shell command Executes a shell command and displays   
#                                       the output in conky. warning: this
#                                       takes a lot more resources than other   
#                                       variables. I'd recommend coding wanted  
#                                       behaviour in C and posting a patch :-). 
#       execbar           shell command Same as exec, except if the first value
#                                       return is a value between 0-100, it
#                                       will use that number for a bar.
#                                       The size for the bar is currently fixed,
#                                       but that may change in the future.
#       execgraph         shell command Same as execbar, but graphs values
#       execi             interval, shell command
#                                       Same as exec but with specific interval.
#                                       Interval can't be less than             
#                                       update_interval in configuration.       
#       font              font          Specify a different font.  Only applies
#                                       to one line.
#       fs_bar            (height), (fs)Bar that shows how much space is used on
#                                       a file system. height is the height in  
#                                       pixels. fs is any file on that file     
#                                       system.                                 
#       fs_free           (fs)          Free space on a file system available   
#                                       for users.                              
#       fs_free_perc      (fs)          Free percentage of space on a file      
#                                       system available for users.             
#       fs_size           (fs)          File system size                        
#       fs_used           (fs)          File system used space                  
#       hr                (height)      Horizontal line, height is the height in
#                                       pixels                                  
#       i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev
#                                       may be omitted if you have only one I2C 
#                                       device. type is either in (or vol)      
#                                       meaning voltage, fan meaning fan or
#                                       temp/tempf (first in C, second in F)
#                                       meaning temperature. n is number of the 
#                                       sensor. See /sys/bus/i2c/devices/ on    
#                                       your local computer.                    
#       if_running        (process)     if PROCESS is running, display
#                                       everything if_running and the matching $endif
#       if_existing       (file)        if FILE exists, display everything between
#                                       if_existing and the matching $endif
#       if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
#                                       if_mounted and the matching $endif
#       else                            Text to show if any of the above are not true
#       kernel                          Kernel version
#       linkstatus        (interface)   Get the link status for wireless connections
#       loadavg           (1), (2), (3) System load average, 1 is for past 1    
#                                       minute, 2 for past 5 minutes and 3 for  
#                                       past 15 minutes.                        
#       machine                         Machine, i686 for example               
#       mails                           Mail count in mail spool. You can use   
#                                       program like fetchmail to get mails from
#                                       some server using your favourite        
#                                       protocol. See also new_mails.           
#       mem                             Amount of memory in use                 
#       membar            (height)      Bar that shows amount of memory in use  
#       memmax                          Total amount of memory                  
#       memperc                         Percentage of memory in use
#
#       metar_ob_time
#       metar_temp
#       metar_tempf                     Temp in F
#       metar_windchill
#       metar_dew_point                 There are a bunch of these
#       metar_rh                        and they are self-explanatory
#       metar_windspeed
#       metar_winddir
#       metar_swinddir
#       metar_cloud
#       metar_u2d_time
#
#       ml_upload_counter               total session upload in mb
#       ml_download_counter             total session download in mb
#       ml_nshared_files                number of shared files
#       ml_shared_counter               total session shared in mb, buggy
#                                       in some mldonkey versions
#       ml_tcp_upload_rate              tcp upload rate in kb/s
#       ml_tcp_download_rate            tcp download rate in kb/s
#       ml_udp_upload_rate              udp upload rate in kb/s
#       ml_udp_download_rate            udp download rate in kb/s
#       ml_ndownloaded_files            number of completed files
#       ml_ndownloading_files           number of downloading files
#
#       mpd_artist                      Artist in current MPD song
#                                       (must be enabled at compile)
#       mpd_album                       Album in current MPD song
#       mpd_bar           (height)      Bar of mpd's progress
#       mpd_bitrate                     Bitrate of current song
#       mpd_status                      Playing, stopped, et cetera.
#       mpd_title                       Title of current MPD song
#       mpd_vol                         MPD's volume
#       mpd_elapsed                     Song's elapsed time
#       mpd_length                      Song's length
#       mpd_percent                     Percent of song's progress
#       new_mails                       Unread mail count in mail spool.        
#       nodename                        Hostname                                
#       outlinecolor      (color)       Change outline color                    
#       pre_exec          shell command Executes a shell command one time before
#                                       conky displays anything and puts output
#                                       as text.                                
#       processes                       Total processes (sleeping and running)  
#       running_processes               Running processes (not sleeping),       
#                                       requires Linux 2.6                      
#       shadecolor        (color)       Change shading color                    
#       stippled_hr       (space),      Stippled (dashed) horizontal line       
#                       (height)
#       swapbar           (height)      Bar that shows amount of swap in use    
#       swap                            Amount of swap in use                   
#       swapmax                         Total amount of swap                    
#       swapperc                        Percentage of swap in use               
#       sysname                         System name, Linux for example          
#       offset            pixels        Move text over by N pixels
#       tail              logfile, lines (interval)
#                                       Displays last N lines of supplied text
#                                       text file.  If interval is not supplied,
#                                       Conky assumes 2x Conky's interval.
#                                       Max of 30 lines.
#                                       Max of 30 lines can be displayed.
#       time              (format)      Local time, see man strftime to get more
#                                       information about format                
#       totaldown         net           Total download, overflows at 4 GB on    
#                                       Linux with 32-bit arch and there doesn't
#                                       seem to be a way to know how many times 
#                                       it has already done that before conky
#                                       has started.
#       top               type, num     This takes arguments in the form:
#                                       top <name> <number>
#                                       Basically, processes are ranked from
#                                       highest to lowest in terms of cpu
#                                       usage, which is what <num> represents.
#                                       The types are: "name", "pid", "cpu", and
#                                       "mem".
#                                       There can be a max of 10 processes listed.
#       top_mem           type, num     Same as top, except sorted by mem usage
#                                       instead of cpu
#       totalup           net           Total upload, this one too, may overflow
#       updates                         Number of updates (for debugging)       
#       upspeed           net           Upload speed in kilobytes               
#       upspeedf          net           Upload speed in kilobytes with one      
#                                       decimal                                 
#       upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
#                                       Upload speed graph, colours defined in
#                                       hex, minus the #.
#       uptime                          Uptime                                  
#       uptime_short                    Uptime in a shorter format              
#

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color white}[${color #00ff00}Jack${color white}] ${color #CCCCCC}@ ${color white}[${color red}$nodename${color white}]:
${color #888888}$sysname $kernel ${color #CCCCCC}on ${color #888888}$machine
${color #888888}Uptime: $uptime
${color #888888}${time %a,}${time %e %B %G}                   ${color #00ff00}${time %H:%M:%S}
${color white}${hr 2}

${color #ffccaa}System:
${color #888888}cpu: ${color #CCCCCC}${freq} MHz
${color #888888}load: ${color #CCCCCC}${cpu}%
${color #888888}${cpugraph 25 ff0000 ff00ff}
${color #888888}ram: ${color #CCCCCC}$mem${color #888888}/${color #CCCCCC}$memmax ${color #888888}, ${color #CCCCCC}$memperc%
${color #888888}swap: ${color #CCCCCC}$swap${color #888888}/${color #CCCCCC}$swapmax ${color #888888}, ${color #CCCCCC}$swapperc%
${color #888888}avg load: (${color #CCCCCC}$loadavg${color #888888})
${color #888888}processes: ${color #CCCCCC}$processes   ${color #888888}running: ${color #CCCCCC}$running_processes
${color white}${hr 1}

${color #ffccaa}Health:
${color #888888}cpu temp: ${color #CCCCCC}${i2c 9191-0290 temp 2} deg
${color #888888}cpu fan speed: ${color #CCCCCC}${i2c 9191-0290 fan 2} rpm
${color #888888}vcore: ${color #CCCCCC}${i2c 9191-0290 in 0}V
${color #888888}mobo temp: ${color #CCCCCC}${i2c 9191-0290 temp 1} deg
${color #888888}mobo fan speed: ${color #CCCCCC}${i2c 9191-0290 fan 3} rpm
${color #888888}gpu temp: ${color #CCCCCC}${execi 300 nvidia-settings -q GPUCoreTemp | grep "xpower:" | cut -d ':' -f3 | cut -d ' ' -f2 | cut -d '.' -f1 ;} deg
${color white}${hr 1}

${color #ffccaa}File Systems:

hda1: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
hdb1: ${fs_used_perc /media/backup}% ${color lightgray}${fs_bar /media/backup/}$color
Swap: $swapperc% ${color lightgray}$swapbar$color

#Weather $color${hr}
#${execi 60 /usr/bin/pymetar CYWH}

This is my /usr/bin/pymetar:

  jack@jack-desktop:~$ cat /usr/bin/pymetar
#!/usr/bin/python2.4 -tt
# -*- coding: iso-8859-15 -*-

__version__="1.0"

import pymetar
import sys

#print "pymet v%s using pymetar lib v%s"%(__version__,pymetar.__version__)

if len(sys.argv)<2 or sys.argv[1]=="--help":
    sys.stderr.write("Usage: %s <station id>\n"% sys.argv[0])
    sys.stderr.write("Station IDs can be found at: http://www.nws.noaa.gov/tg/siteloc.shtml\n")
    sys.exit(1)
elif (sys.argv[1] == "--version"):
    print "pmw v%s using pymetar lib v%s"%(__version__,pymetar.__version__)
    sys.exit(0)
else:
    station=sys.argv[1]

try:
    rf=pymetar.ReportFetcher(station)
    rep=rf.FetchReport()
except Exception, e:
    sys.stderr.write("Something went wrong when fetching the report.\n")
    sys.stderr.write("These usually are transient problems if the station ")
    sys.stderr.write("ID is valid. \nThe error encountered was:\n")
    sys.stderr.write(str(e)+"\n")
    sys.exit(1)

Not sure what it means by too many values to unpack?

---

