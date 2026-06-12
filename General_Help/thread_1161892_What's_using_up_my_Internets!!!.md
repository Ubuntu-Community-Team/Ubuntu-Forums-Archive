---
title: "What's using up my Internets???!!!"
date: 2009-05-17
forum: General Help
---

### Post by glubbdrubb on 2009-05-17
Sorry about the title of this thread but this issue is affecting my english.

I keep the "System Monitor" open on one of my monitor screens. Recently I noticed a constant "stream" like traffic in the "Network History" graph. (it looks as if I am stream audio or video from the web, as I do occasionally). I close all obvious applications (other than System Monitor" and notice it's still chugging down the killobits. I reboot and check running processes (all processes), but I don't see anything unusual there. 

It usually ranges between 15 to 30 Kbps down and 5 or 6 Kbps up. This is the maximum my ADSL connection gives me anyway.

I paste here the output of the netstat command:
(I suspect I am missing stuff from the top of the output but I don't know how to control it)


```

unix  3      [ ]         STREAM     CONNECTED     23063    
unix  3      [ ]         STREAM     CONNECTED     23062    /tmp/orbit-victor/linc-1e12-0-51a5e8d22d7c2
unix  3      [ ]         STREAM     CONNECTED     23061    
unix  3      [ ]         STREAM     CONNECTED     23060    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     23059    
unix  3      [ ]         STREAM     CONNECTED     23058    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     23057    
unix  3      [ ]         STREAM     CONNECTED     23137    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     22965    
unix  27     [ ]         STREAM     CONNECTED     22963    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22962    
unix  3      [ ]         STREAM     CONNECTED     23052    /tmp/orbit-victor/linc-1e12-0-51a5e8d22d7c2
unix  3      [ ]         STREAM     CONNECTED     22854    
unix  3      [ ]         STREAM     CONNECTED     22851    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22850    
unix  27     [ ]         STREAM     CONNECTED     22849    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22848    
unix  3      [ ]         STREAM     CONNECTED     22838    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22837    
unix  3      [ ]         STREAM     CONNECTED     22828    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22827    
unix  3      [ ]         STREAM     CONNECTED     22656    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22655    
unix  3      [ ]         STREAM     CONNECTED     24126    /tmp/orbit-victor/linc-1e10-0-2e970b8ce7efc
unix  3      [ ]         STREAM     CONNECTED     22654    
unix  3      [ ]         STREAM     CONNECTED     22651    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22650    
unix  27     [ ]         STREAM     CONNECTED     22649    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22648    
unix  3      [ ]         STREAM     CONNECTED     22644    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22643    
unix  3      [ ]         STREAM     CONNECTED     22604    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22603    
unix  3      [ ]         STREAM     CONNECTED     23136    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     22600    
unix  3      [ ]         STREAM     CONNECTED     23288    /tmp/orbit-victor/linc-1e0f-0-1b9b98d0cade4
unix  3      [ ]         STREAM     CONNECTED     22599    
unix  3      [ ]         STREAM     CONNECTED     22596    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22595    
unix  27     [ ]         STREAM     CONNECTED     22594    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22593    
unix  3      [ ]         STREAM     CONNECTED     22589    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22588    
unix  3      [ ]         STREAM     CONNECTED     22545    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22544    
unix  3      [ ]         STREAM     CONNECTED     22383    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22382    
unix  3      [ ]         STREAM     CONNECTED     22381    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22380    
unix  3      [ ]         STREAM     CONNECTED     22379    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     22378    
unix  3      [ ]         STREAM     CONNECTED     22377    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22376    
unix  3      [ ]         STREAM     CONNECTED     22375    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     22374    
unix  3      [ ]         STREAM     CONNECTED     22373    /tmp/orbit-victor/linc-1df6-0-65e0820e7190
unix  3      [ ]         STREAM     CONNECTED     22372    
unix  3      [ ]         STREAM     CONNECTED     22371    /tmp/orbit-victor/linc-1df9-0-1aa0bd838624a
unix  3      [ ]         STREAM     CONNECTED     22370    
unix  3      [ ]         STREAM     CONNECTED     22368    /tmp/orbit-victor/linc-1df6-0-65e0820e7190
unix  3      [ ]         STREAM     CONNECTED     22367    
unix  3      [ ]         STREAM     CONNECTED     22366    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     22365    
unix  3      [ ]         STREAM     CONNECTED     22364    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     22363    
unix  3      [ ]         STREAM     CONNECTED     22362    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22361    
unix  3      [ ]         STREAM     CONNECTED     22358    /tmp/orbit-victor/linc-1df6-0-65e0820e7190
unix  3      [ ]         STREAM     CONNECTED     22357    
unix  3      [ ]         STREAM     CONNECTED     22355    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     22354    
unix  3      [ ]         STREAM     CONNECTED     22353    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22352    
unix  3      [ ]         STREAM     CONNECTED     22350    
unix  3      [ ]         STREAM     CONNECTED     22349    
unix  3      [ ]         STREAM     CONNECTED     22347    
unix  3      [ ]         STREAM     CONNECTED     22346    
unix  2      [ ]         STREAM     CONNECTED     22345    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     22356    /tmp/orbit-victor/linc-1df6-0-65e0820e7190
unix  3      [ ]         STREAM     CONNECTED     22293    
unix  3      [ ]         STREAM     CONNECTED     22290    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22289    
unix  27     [ ]         STREAM     CONNECTED     22288    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22287    
unix  3      [ ]         STREAM     CONNECTED     22283    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22282    
unix  3      [ ]         STREAM     CONNECTED     22277    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22276    
unix  3      [ ]         STREAM     CONNECTED     22275    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22274    
unix  3      [ ]         STREAM     CONNECTED     22270    /tmp/orbit-victor/linc-1df9-0-1aa0bd838624a
unix  3      [ ]         STREAM     CONNECTED     22269    
unix  3      [ ]         STREAM     CONNECTED     22268    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     22267    
unix  3      [ ]         STREAM     CONNECTED     22266    /tmp/orbit-victor/linc-1df9-0-1aa0bd838624a
unix  3      [ ]         STREAM     CONNECTED     22265    
unix  3      [ ]         STREAM     CONNECTED     22262    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     22261    
unix  3      [ ]         STREAM     CONNECTED     22260    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22259    
unix  27     [ ]         STREAM     CONNECTED     22258    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22257    
unix  3      [ ]         STREAM     CONNECTED     22253    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22252    
unix  3      [ ]         STREAM     CONNECTED     22167    @/dbus-vfs-daemon/socket-92vW0vzs
unix  3      [ ]         STREAM     CONNECTED     22166    
unix  3      [ ]         STREAM     CONNECTED     22168    @/dbus-vfs-daemon/socket-UwGCrFiL
unix  3      [ ]         STREAM     CONNECTED     22165    
unix  3      [ ]         STREAM     CONNECTED     22158    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22157    
unix  3      [ ]         STREAM     CONNECTED     22136    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22135    
unix  3      [ ]         STREAM     CONNECTED     22130    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22129    
unix  3      [ ]         STREAM     CONNECTED     22127    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     22126    
unix  3      [ ]         STREAM     CONNECTED     22125    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22124    
unix  3      [ ]         STREAM     CONNECTED     22119    @/dbus-vfs-daemon/socket-8cFpoQtG
unix  3      [ ]         STREAM     CONNECTED     22117    
unix  3      [ ]         STREAM     CONNECTED     22118    @/dbus-vfs-daemon/socket-No7yKJOV
unix  3      [ ]         STREAM     CONNECTED     22116    
unix  3      [ ]         STREAM     CONNECTED     22111    @/dbus-vfs-daemon/socket-kDYp0GEp
unix  3      [ ]         STREAM     CONNECTED     22110    
unix  3      [ ]         STREAM     CONNECTED     22109    @/dbus-vfs-daemon/socket-jVNfmTpZ
unix  3      [ ]         STREAM     CONNECTED     22108    
unix  3      [ ]         STREAM     CONNECTED     22105    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22104    
unix  3      [ ]         STREAM     CONNECTED     22102    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     22101    
unix  3      [ ]         STREAM     CONNECTED     22100    /tmp/orbit-victor/linc-1de7-0-3ed0f2b138737
unix  3      [ ]         STREAM     CONNECTED     22099    
unix  3      [ ]         STREAM     CONNECTED     22097    @/dbus-vfs-daemon/socket-OXchteVB
unix  3      [ ]         STREAM     CONNECTED     22096    
unix  3      [ ]         STREAM     CONNECTED     22098    @/dbus-vfs-daemon/socket-kP4M1g1b
unix  3      [ ]         STREAM     CONNECTED     22095    
unix  3      [ ]         STREAM     CONNECTED     22089    @/dbus-vfs-daemon/socket-Asffmka6
unix  3      [ ]         STREAM     CONNECTED     22088    
unix  3      [ ]         STREAM     CONNECTED     22090    @/dbus-vfs-daemon/socket-CV9tQIlV
unix  3      [ ]         STREAM     CONNECTED     22087    
unix  3      [ ]         STREAM     CONNECTED     22084    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22083    
unix  3      [ ]         STREAM     CONNECTED     22079    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22078    
unix  3      [ ]         STREAM     CONNECTED     22057    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22056    
unix  3      [ ]         STREAM     CONNECTED     22055    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22054    
unix  3      [ ]         STREAM     CONNECTED     22053    /tmp/orbit-victor/linc-1de7-0-3ed0f2b138737
unix  3      [ ]         STREAM     CONNECTED     22052    
unix  3      [ ]         STREAM     CONNECTED     22051    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     22050    
unix  3      [ ]         STREAM     CONNECTED     22049    /tmp/orbit-victor/linc-1de7-0-3ed0f2b138737
unix  3      [ ]         STREAM     CONNECTED     22048    
unix  3      [ ]         STREAM     CONNECTED     22045    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     22044    
unix  3      [ ]         STREAM     CONNECTED     22043    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     22042    
unix  27     [ ]         STREAM     CONNECTED     22041    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22040    
unix  3      [ ]         STREAM     CONNECTED     22036    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22035    
unix  3      [ ]         STREAM     CONNECTED     21997    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21996    
unix  3      [ ]         STREAM     CONNECTED     21995    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21994    
unix  3      [ ]         STREAM     CONNECTED     21986    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21985    
unix  3      [ ]         STREAM     CONNECTED     21984    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21983    
unix  3      [ ]         STREAM     CONNECTED     21982    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21981    
unix  3      [ ]         STREAM     CONNECTED     21973    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21972    
unix  3      [ ]         STREAM     CONNECTED     21971    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21970    
unix  3      [ ]         STREAM     CONNECTED     21969    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     21968    
unix  3      [ ]         STREAM     CONNECTED     21966    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21965    
unix  3      [ ]         STREAM     CONNECTED     21964    /tmp/orbit-victor/linc-1dda-0-3721ee0d135c8
unix  3      [ ]         STREAM     CONNECTED     21963    
unix  3      [ ]         STREAM     CONNECTED     21962    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     21961    
unix  3      [ ]         STREAM     CONNECTED     21958    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21957    
unix  3      [ ]         STREAM     CONNECTED     21955    /tmp/orbit-victor/linc-1dda-0-3721ee0d135c8
unix  3      [ ]         STREAM     CONNECTED     21954    
unix  3      [ ]         STREAM     CONNECTED     21952    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21951    
unix  3      [ ]         STREAM     CONNECTED     21950    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21949    
unix  3      [ ]         STREAM     CONNECTED     21948    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     21947    
unix  3      [ ]         STREAM     CONNECTED     21953    /tmp/orbit-victor/linc-1dda-0-3721ee0d135c8
unix  3      [ ]         STREAM     CONNECTED     21946    
unix  3      [ ]         STREAM     CONNECTED     21943    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21942    
unix  27     [ ]         STREAM     CONNECTED     21941    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21940    
unix  3      [ ]         STREAM     CONNECTED     21936    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21935    
unix  3      [ ]         STREAM     CONNECTED     21929    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     21928    
unix  3      [ ]         STREAM     CONNECTED     21927    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     21926    
unix  3      [ ]         STREAM     CONNECTED     21901    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     21900    
unix  3      [ ]         STREAM     CONNECTED     21898    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21897    
unix  3      [ ]         STREAM     CONNECTED     21896    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21895    
unix  3      [ ]         STREAM     CONNECTED     21822    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     21821    
unix  3      [ ]         STREAM     CONNECTED     21899    /tmp/orbit-victor/linc-1dd8-0-4465e88fb6742
unix  3      [ ]         STREAM     CONNECTED     21820    
unix  3      [ ]         STREAM     CONNECTED     21817    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21816    
unix  27     [ ]         STREAM     CONNECTED     21815    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21814    
unix  3      [ ]         STREAM     CONNECTED     21810    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21809    
unix  2      [ ]         DGRAM                    21773    
unix  3      [ ]         STREAM     CONNECTED     21765    /tmp/orbit-victor/linc-1dd7-0-56a795127efc3
unix  3      [ ]         STREAM     CONNECTED     21764    
unix  3      [ ]         STREAM     CONNECTED     21762    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21761    
unix  3      [ ]         STREAM     CONNECTED     21760    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21759    
unix  3      [ ]         STREAM     CONNECTED     21763    /tmp/orbit-victor/linc-1dd7-0-56a795127efc3
unix  3      [ ]         STREAM     CONNECTED     21758    
unix  3      [ ]         STREAM     CONNECTED     21755    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21754    
unix  27     [ ]         STREAM     CONNECTED     21753    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21752    
unix  3      [ ]         STREAM     CONNECTED     21748    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21747    
unix  3      [ ]         STREAM     CONNECTED     21741    /tmp/orbit-victor/linc-1dd5-0-63b717d960cb5
unix  3      [ ]         STREAM     CONNECTED     21740    
unix  3      [ ]         STREAM     CONNECTED     21737    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21736    
unix  3      [ ]         STREAM     CONNECTED     21730    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21729    
unix  4      [ ]         STREAM     CONNECTED     21725    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21724    
unix  3      [ ]         STREAM     CONNECTED     21723    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     21722    
unix  3      [ ]         STREAM     CONNECTED     21691    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21690    
unix  3      [ ]         STREAM     CONNECTED     21689    /tmp/orbit-victor/linc-1dba-0-836e703b61ef
unix  3      [ ]         STREAM     CONNECTED     21688    
unix  3      [ ]         STREAM     CONNECTED     21686    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21685    
unix  3      [ ]         STREAM     CONNECTED     21684    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21683    
unix  3      [ ]         STREAM     CONNECTED     21687    /tmp/orbit-victor/linc-1dba-0-836e703b61ef
unix  3      [ ]         STREAM     CONNECTED     21682    
unix  3      [ ]         STREAM     CONNECTED     21679    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21678    
unix  27     [ ]         STREAM     CONNECTED     21677    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21676    
unix  3      [ ]         STREAM     CONNECTED     21640    /tmp/orbit-victor/linc-1d80-0-6a50f4ff92245
unix  3      [ ]         STREAM     CONNECTED     21639    
unix  3      [ ]         STREAM     CONNECTED     21638    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21637    
unix  27     [ ]         STREAM     CONNECTED     21636    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21635    
unix  3      [ ]         STREAM     CONNECTED     21634    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21633    
unix  3      [ ]         STREAM     CONNECTED     21526    /tmp/orbit-victor/linc-1d74-0-6f3f04faf08d4
unix  3      [ ]         STREAM     CONNECTED     21525    
unix  3      [ ]         STREAM     CONNECTED     21524    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21523    
unix  28     [ ]         STREAM     CONNECTED     21522    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21521    
unix  3      [ ]         STREAM     CONNECTED     21520    /tmp/orbit-victor/linc-1d2a-0-48d8f3c676bc
unix  3      [ ]         STREAM     CONNECTED     21519    
unix  3      [ ]         STREAM     CONNECTED     21518    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21517    
unix  28     [ ]         STREAM     CONNECTED     21516    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21515    
unix  3      [ ]         STREAM     CONNECTED     21402    /tmp/orbit-victor/linc-1d7f-0-7e828d56a3adf
unix  3      [ ]         STREAM     CONNECTED     21401    
unix  3      [ ]         STREAM     CONNECTED     21400    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21399    
unix  3      [ ]         STREAM     CONNECTED     21398    /tmp/orbit-victor/linc-1d82-0-54340f22a37ae
unix  3      [ ]         STREAM     CONNECTED     21395    
unix  3      [ ]         STREAM     CONNECTED     21363    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     21362    
unix  3      [ ]         STREAM     CONNECTED     21359    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21358    
unix  3      [ ]         STREAM     CONNECTED     21333    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21332    
unix  3      [ ]         STREAM     CONNECTED     21330    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21329    
unix  3      [ ]         STREAM     CONNECTED     21310    /tmp/orbit-victor/linc-1d74-0-6f3f04faf08d4
unix  3      [ ]         STREAM     CONNECTED     21309    
unix  3      [ ]         STREAM     CONNECTED     21306    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21305    
unix  3      [ ]         STREAM     CONNECTED     21301    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21300    
unix  3      [ ]         STREAM     CONNECTED     21269    /tmp/orbit-victor/linc-1d80-0-6a50f4ff92245
unix  3      [ ]         STREAM     CONNECTED     21268    
unix  3      [ ]         STREAM     CONNECTED     21265    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21264    
unix  28     [ ]         STREAM     CONNECTED     21237    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21236    
unix  3      [ ]         STREAM     CONNECTED     21234    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21233    
unix  3      [ ]         STREAM     CONNECTED     21227    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21226    
unix  3      [ ]         STREAM     CONNECTED     21225    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21224    
unix  3      [ ]         STREAM     CONNECTED     21220    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21219    
unix  3      [ ]         STREAM     CONNECTED     21195    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21194    
unix  3      [ ]         STREAM     CONNECTED     21200    /tmp/.ICE-unix/7466
unix  3      [ ]         STREAM     CONNECTED     21160    
unix  3      [ ]         STREAM     CONNECTED     21154    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21153    
unix  3      [ ]         STREAM     CONNECTED     21066    /tmp/orbit-victor/linc-1d2a-0-48d8f3c676bc
unix  3      [ ]         STREAM     CONNECTED     21065    
unix  3      [ ]         STREAM     CONNECTED     21062    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     21061    
unix  3      [ ]         STREAM     CONNECTED     21025    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     21024    
unix  3      [ ]         STREAM     CONNECTED     21022    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21021    
unix  3      [ ]         STREAM     CONNECTED     20997    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20996    
unix  3      [ ]         STREAM     CONNECTED     20989    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20988    
unix  3      [ ]         STREAM     CONNECTED     20987    /tmp/orbit-victor/linc-1d6c-0-bbf210d49c97
unix  3      [ ]         STREAM     CONNECTED     20986    
unix  3      [ ]         STREAM     CONNECTED     20983    /tmp/orbit-victor/linc-1d6e-0-1223e09032cf5
unix  3      [ ]         STREAM     CONNECTED     20982    
unix  3      [ ]         STREAM     CONNECTED     20976    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20975    
unix  3      [ ]         STREAM     CONNECTED     20697    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     20696    
unix  3      [ ]         STREAM     CONNECTED     20683    @/tmp/dbus-mmeLgopkGQ
unix  3      [ ]         STREAM     CONNECTED     20682    
unix  3      [ ]         STREAM     CONNECTED     20639    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20638    
unix  3      [ ]         STREAM     CONNECTED     20614    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20613    
unix  3      [ ]         STREAM     CONNECTED     20609    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20608    
unix  3      [ ]         STREAM     CONNECTED     20607    
unix  3      [ ]         STREAM     CONNECTED     20606    
unix  28     [ ]         STREAM     CONNECTED     20593    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20592    
unix  3      [ ]         STREAM     CONNECTED     20399    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20398    
unix  3      [ ]         STREAM     CONNECTED     20369    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20368    
unix  26     [ ]         STREAM     CONNECTED     20103    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20100    
unix  3      [ ]         STREAM     CONNECTED     20099    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20098    
unix  3      [ ]         STREAM     CONNECTED     19630    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19629    
unix  3      [ ]         STREAM     CONNECTED     19312    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19311    
unix  2      [ ]         DGRAM                    19266    
unix  3      [ ]         STREAM     CONNECTED     19263    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19262    
unix  3      [ ]         STREAM     CONNECTED     19175    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19174    
unix  2      [ ]         DGRAM                    19170    
unix  3      [ ]         STREAM     CONNECTED     19035    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19034    
unix  2      [ ]         DGRAM                    19016    
unix  3      [ ]         STREAM     CONNECTED     18802    @/var/run/hald/dbus-tGCwAXLOuE
unix  3      [ ]         STREAM     CONNECTED     18801    
unix  3      [ ]         STREAM     CONNECTED     18800    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18799    
unix  2      [ ]         DGRAM                    18650    
unix  3      [ ]         STREAM     CONNECTED     18649    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18648    
unix  3      [ ]         STREAM     CONNECTED     18643    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18642    
unix  3      [ ]         STREAM     CONNECTED     18641    @/var/run/hald/dbus-tGCwAXLOuE
unix  3      [ ]         STREAM     CONNECTED     18638    
unix  3      [ ]         STREAM     CONNECTED     18640    @/var/run/hald/dbus-tGCwAXLOuE
unix  3      [ ]         STREAM     CONNECTED     18624    
unix  3      [ ]         STREAM     CONNECTED     18585    @/var/run/hald/dbus-tGCwAXLOuE
unix  3      [ ]         STREAM     CONNECTED     18584    
unix  3      [ ]         STREAM     CONNECTED     18302    @/var/run/hald/dbus-nsOsufchWn
unix  3      [ ]         STREAM     CONNECTED     18291    
unix  3      [ ]         STREAM     CONNECTED     18273    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18272    
unix  3      [ ]         STREAM     CONNECTED     18261    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18260    
unix  3      [ ]         STREAM     CONNECTED     18234    
unix  3      [ ]         STREAM     CONNECTED     18233    
unix  3      [ ]         STREAM     CONNECTED     17052    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17051    
unix  3      [ ]         STREAM     CONNECTED     17046    
unix  3      [ ]         STREAM     CONNECTED     17045    
unix  2      [ ]         DGRAM                    17043    
unix  3      [ ]         STREAM     CONNECTED     17000    
unix  3      [ ]         STREAM     CONNECTED     16999    
unix  2      [ ]         DGRAM                    16929    

```
I apologize if it does not come out nicely, I am still getting the hang of the formatting... My username is victor.


I then did a port-scan of 127.0.0.1 using Network Tools and got this:

139   open netbios-ssn
445   open microsoft-ds
631   open ipp
40054 open unkown
59635 open unkown

(I hand typed that part)

Is it possible a that a Windows virus is running in Wine? What app could be downloading all this?

I live in South Africa and data is very expensive; we pay per megabyte, so this really needs to be solved. 

Thanks

---

### Post by glubbdrubb on 2009-05-17
Crises Over!

It turn out an XP computer on the LAN has been trying to print to my shared printer(port 631) but fails. A simple restart did the trick.

Now can someone explain to me why the output of netsat in Network Tools is so much shorter than when using the Terminal? Windows has a useful tool called TcpVeiw which lists connections really nicely. An equivalent on Ubuntu would be nice.

---

