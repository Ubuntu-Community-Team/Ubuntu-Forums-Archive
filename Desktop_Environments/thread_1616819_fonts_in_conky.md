---
title: "fonts in conky"
date: 2010-11-08
forum: Desktop Environments
---

### Post by tommah04 on 2010-11-08
hello,

I just started using conky and am getting the hang of it (quite awesome once its up and running).  and got everything I like (very basic but nice) and the only thing I really wanna change or play with is the font.  I try to change it to a couple custom fonts I downloaded and installed usr/font/truetype, but cannot get them to show.  They just come out looking exactly like everything else.

ubuntu 10.10 amd 64





background no
use_xft yes
xftfont atomico:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color red
default_outline_color green
alignment top_left
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes
text_buffer_size 256

# Possible variables to be used:
#
#      Variable         Arguments                  Description                

#     addr              (interface)   IP address for an interface
#     acpiacadapter                   ACPI ac adapter state.                   
#     acpifan                         ACPI fan state                           
#     acpitemp                        ACPI temperature.                        
#     adt746xcpu                      CPU temperature from therm_adt746x       
#     adt746xfan                      Fan speed from therm_adt746x             
#     alignr            (num)         Right-justify text, with space of N
#     alignc                          Align text to centre
#     battery           (num)         Remaining capasity in ACPI or APM        
#                     battery. ACPI battery number can be      
#                     given as argument (default is BAT0).     
#     buffers                         Amount of memory buffered                
#     cached                          Amount of memory cached                  
#     color             (color)       Change drawing color to color            
#     cpu                             CPU usage in percents                    
#     cpubar            (height)      Bar that shows CPU usage, height is      
#                     bar's height in pixels                 
#     cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
#                     CPU usage graph, with optional colours in hex,
#                     minus the #.
#     downspeed         net           Download speed in kilobytes              
#     downspeedf        net           Download speed in kilobytes with one     
#                     decimal                                  
#     downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
#                     Download speed graph, colours defined in
#                     hex, minus the #.
#     exec              shell command Executes a shell command and displays    
#                     the output in conky. warning: this      
#                     takes a lot more resources than other    
#                     variables. I'd recommend coding wanted   
#                     behaviour in C and posting a patch :-).  
#     execbar           shell command Same as exec, except if the first value
#                     return is a value between 0-100, it
#                     will use that number for a bar.
#                     The size for the bar is currently fixed,
#                     but that may change in the future.
#     execgraph         shell command Same as execbar, but graphs values
#     execi             interval, shell command
#                      Same as exec but with specific interval. 
#                     Interval can't be less than              
#                     update_interval in configuration.        
#    font          font        Specify a different font.  Only applies
#                    to one line.
#     fs_bar            (height), (fs)Bar that shows how much space is used on 
#                     a file system. height is the height in   
#                     pixels. fs is any file on that file      
#                     system.                                  
#     fs_free           (fs)          Free space on a file system available    
#                     for users.                               
#     fs_free_perc      (fs)          Free percentage of space on a file       
#                     system available for users.              
#     fs_size           (fs)          File system size                         
#     fs_used           (fs)          File system used space                   
#     hr                (height)      Horizontal line, height is the height in 
#                     pixels                                   
#     i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                     may be omitted if you have only one I2C  
#                     device. type is either in (or vol)       
#                     meaning voltage, fan meaning fan or
#                     temp/tempf (first in C, second in F)
#                     meaning temperature. n is number of the  
#                     sensor. See /sys/bus/i2c/devices/ on     
#                     your local computer.                     
#     if_running        (process)     if PROCESS is running, display
#                     everything if_running and the matching $endif
#     if_existing       (file)        if FILE exists, display everything between
#                     if_existing and the matching $endif
#     if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
#                     if_mounted and the matching $endif
#     else                            Text to show if any of the above are not true
#     kernel                          Kernel version                          
#     linkstatus        (interface)   Get the link status for wireless connections
#     loadavg           (1), (2), (3) System load average, 1 is for past 1     
#                     minute, 2 for past 5 minutes and 3 for   
#                     past 15 minutes.                         
#     machine                         Machine, i686 for example                
#     mails                           Mail count in mail spool. You can use    
#                     program like fetchmail to get mails from 
#                     some server using your favourite         
#                     protocol. See also new_mails.            
#     mem                             Amount of memory in use                  
#     membar            (height)      Bar that shows amount of memory in use   
#     memmax                          Total amount of memory                   
#     memperc                         Percentage of memory in use
#     
#     metar_ob_time
#     metar_temp
#     metar_tempf                     Temp in F
#     metar_windchill
#     metar_dew_point                 There are a bunch of these
#     metar_rh                        and they are self-explanatory
#     metar_windspeed
#     metar_winddir
#     metar_swinddir
#     metar_cloud
#     metar_u2d_time
#     
#     ml_upload_counter               total session upload in mb
#     ml_download_counter             total session download in mb
#     ml_nshared_files                number of shared files
#     ml_shared_counter               total session shared in mb, buggy
#                     in some mldonkey versions
#     ml_tcp_upload_rate              tcp upload rate in kb/s
#     ml_tcp_download_rate            tcp download rate in kb/s
#     ml_udp_upload_rate              udp upload rate in kb/s
#     ml_udp_download_rate            udp download rate in kb/s
#     ml_ndownloaded_files            number of completed files
#     ml_ndownloading_files           number of downloading files
#     
#     mpd_artist            Artist in current MPD song
#                     (must be enabled at compile)
#     mpd_album            Album in current MPD song
#     mpd_bar           (height)      Bar of mpd's progress
#     mpd_bitrate                     Bitrate of current song
#     mpd_status                      Playing, stopped, et cetera.
#     mpd_title            Title of current MPD song
#     mpd_vol                MPD's volume
#     mpd_elapsed                     Song's elapsed time
#     mpd_length                      Song's length
#     mpd_percent                     Percent of song's progress
#     new_mails                       Unread mail count in mail spool.         
#     nodename                        Hostname                                 
#     outlinecolor      (color)       Change outline color                     
#     pre_exec          shell command Executes a shell command one time before 
#                     conky displays anything and puts output 
#                     as text.                                 
#     processes                       Total processes (sleeping and running)   
#     running_processes               Running processes (not sleeping),        
#                     requires Linux 2.6                       
#     shadecolor        (color)       Change shading color                     
#     stippled_hr       (space),      Stippled (dashed) horizontal line        
#             (height)        
#     swapbar           (height)      Bar that shows amount of swap in use     
#     swap                            Amount of swap in use                    
#     swapmax                         Total amount of swap                     
#     swapperc                        Percentage of swap in use                
#     sysname                         System name, Linux for example           
#     offset            pixels        Move text over by N pixels
#     tail              logfile, lines (interval)
#                     Displays last N lines of supplied text
#                     text file.  If interval is not supplied,
#                     Conky assumes 2x Conky's interval.
#                     Max of 30 lines.
#                     Max of 30 lines can be displayed.
#     time              (format)      Local time, see man strftime to get more 
#                     information about format                 
#     totaldown         net           Total download, overflows at 4 GB on     
#                     Linux with 32-bit arch and there doesn't 
#                     seem to be a way to know how many times  
#                     it has already done that before conky   
#                     has started.                            
#     top               type, num     This takes arguments in the form:
#                     top <name> <number>
#                     Basically, processes are ranked from 
#                     highest to lowest in terms of cpu
#                     usage, which is what <num> represents.
#                     The types are: "name", "pid", "cpu", and
#                     "mem".
#                     There can be a max of 10 processes listed.
#     top_mem           type, num     Same as top, except sorted by mem usage
#                     instead of cpu
#     totalup           net           Total upload, this one too, may overflow 
#     updates                         Number of updates (for debugging)        
#     upspeed           net           Upload speed in kilobytes                
#     upspeedf          net           Upload speed in kilobytes with one       
#                     decimal                                  
#     upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
#                     Upload speed graph, colours defined in
#                     hex, minus the #.
#     uptime                          Uptime                                   
#     uptime_short                    Uptime in a shorter format               
#     
#     seti_prog                       Seti@home current progress
#     seti_progbar      (height)      Seti@home current progress bar
#     seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen


TEXT
${font Arial:size=12}${execi 300 date +"%B %Y"}
${font FFF_Tusj:size=22}${time %r}${font}

${font  atomico:size=10}SYSTEM${hr 2}${font}
${font atomico:size=8}$sysname $kernel $alignr $machine
AMD Athlon II X3 $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
 

${font atomico:size=10}PROCESSORS${hr 2}${font}
${font atomico:size=8}CPU0  ${cpu cpu0}% ${cpubar cpu0}
${font atomico:size=8}CPU1  ${cpu cpu1}% ${cpubar cpu1}
${font atomico:size=8}CPU2  ${cpu cpu2}% ${cpubar cpu2}
${font atomico:size=8}CPU3  ${cpu cpu3}% ${cpubar cpu3}

${font atomico:size=10}RAM${hr 2}
${font atomico:size=8}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${font atomico:size=10}HDD${hr 2}
${font atomico:size=8}Home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
Storage $alignc ${fs_used /media/Storage} / ${fs_size /media/Storage} $alignr ${fs_free_perc /media/Storage}%
${fs_bar /media/Storage}
Win7 $alignc ${fs_used /media/E478286C78284022} / ${fs_size /media/E478286C78284022} $alignr ${fs_free_perc /media/E478286C78284022}%
${fs_bar /media/E478286C78284022}

${font atomico:size=10}TOP PROCESSES${hr 2}
${font atomico:size=8}${top_mem name 2}${alignr}${top mem 2} %
${font atomico:size=8}${top_mem name 3}${alignr}${top mem 3} %
${font atomico:size=8}${top_mem name 4}${alignr}${top mem 4} %
${font atomico:size=8}${top_mem name 5}${alignr}${top mem 5} %

---

### Post by cipherboy_loc on 2010-11-08
Did you install the fonts? Use [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) 's second method. 


Cipherboy

---

### Post by tommah04 on 2010-11-08
yes, that's how I installed it

---

### Post by stinkeye on 2010-11-09
The actual name of the font is ...
```
ATÔMICO
```
using the latin capital O with circumflex.
ATÔMICO font doesn't have any numbers in it.


Use the gedit search and replace tool to search for 
```
atomico
```

and replace with
```
ATÔMICO
```


If you don't need to install fonts system wide (ie for other users)
I just put fonts into **~/.fonts** so when I backup my home directory the added fonts are backed up.

P.S
Please use code blocks for pasting long configs etc.
Click on the # symbol and paste between the code blocks.

---

### Post by tommah04 on 2010-11-16
thanks, this worked... also thanks for the code blocks.  never knew how to do that

---

### Post by stinkeye on 2010-11-16
No problem.
Careful with conky.
It's addictive.
There's a thread here of nearly 1500 pages for conkaholics.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=1477[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=1477")

---

### Post by tommah04 on 2010-11-18
oh I know!  its so cool!

---

