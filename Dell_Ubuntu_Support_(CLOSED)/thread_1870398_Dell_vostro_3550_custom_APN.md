---
title: "Dell vostro 3550 custom APN"
date: 2011-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rob.kennedy.za on 2011-10-27
Hi all

Im having endless issues with the vostro and connecting on a custom APN. I have tested the sim card on another machine and connect to the APN fine.

Please see logs bellow

Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) starting connection 'APN'
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> (wwan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) started...
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.172732] [nm-agent-manager.c:1100] nm_agent_manager_get_secrets(): Secrets requested for connection /org/freedesktop/NetworkManager/Settings/16 (gsm)
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.172757] [nm-agent-manager.c:619] request_add_agent(): (:1.66/org.gnome.Shell.NetworkAgent/1000) agent allowed for secrets request 0x87bb40/gsm
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.172771] [nm-agent-manager.c:619] request_add_agent(): (:1.45/org.freedesktop.nm-applet/1000) agent allowed for secrets request 0x87bb40/gsm
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.172790] [nm-settings-connection.c:864] nm_settings_connection_get_secrets(): (51898d17-1f27-4d8e-9869-9a53b7bbc86c/gsm:12) secrets requested flags 0x1 hint 'password'
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> (wwan0): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) complete.
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.173260] [nm-agent-manager.c:1015] get_start(): (0x87bb40/gsm) system settings secrets sufficient
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.173282] [nm-settings-connection.c:721] agent_secrets_done_cb(): (51898d17-1f27-4d8e-9869-9a53b7bbc86c/gsm:12) existing secrets returned
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.173294] [nm-settings-connection.c:727] agent_secrets_done_cb(): (51898d17-1f27-4d8e-9869-9a53b7bbc86c/gsm:12) secrets request completed
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <debug> [1319712785.174214] [nm-settings-connection.c:767] agent_secrets_done_cb(): (51898d17-1f27-4d8e-9869-9a53b7bbc86c/gsm:12) new agent secrets processed
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) started...
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> (wwan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 27 12:53:05 robertk-laptop NetworkManager[1139]: <info> Activation (wwan0) Stage 1 of 5 (Device Prepare) complete.
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): number => "*99#"
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): username => "robert.k@vb.onlinedirect.co.za"
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): password => "*******"
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): apn => "vb.onlinedirect.co.za"
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): network_mode => 0
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:5099] simple_connect(): (wwan0): allowed_mode => 0
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:4988] simple_state_machine(): (wwan0): simple connect state 0
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:4988] simple_state_machine(): (wwan0): simple connect state 2
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CREG?<CR>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>+CREG: 2,1,"0098","00003A49"<CR><LF>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:4988] simple_state_machine(): (wwan0): simple connect state 4
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT+CGDCONT?<CR>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>+CGDCONT: 1,"IP","vb.onlinedirect.co.za","0.0.0.0",0,0<CR><LF>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '+CGDCONT: 2,"IP","internet","0.0.0.0",0,0<CR><LF>+CGDCONT: 3,"IP","vb.onlinedirectsa.co.za","0.0.0.0",0,0<CR><LF>+CGDCONT: 4,"IP","onlinedirect.co.za","0.0.0.0",0,0<CR><LF>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-generic-gsm.c:4988] simple_state_machine(): (wwan0): simple connect state 5
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <info>  [mm-modem.c:742] mm_modem_set_state(): Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Oct 27 12:53:05 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT*EIAAUW=1,1,"robert.k@vb.onlinedirect.co.za","******"<CR>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT*E2NAP=1<CR>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT*ENAP=1,1<CR>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>*E2NAP: 2<CR><LF>'
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-modem-mbm.c:706] mbm_e2nap_received(): connecting
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236121] [nm-device-wifi.c:856] get_active_ap(): (wlan0): active BSSID: 00:02:6f:af:97:20
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236230] [nm-device-wifi.c:866] get_active_ap(): (wlan0): active SSID: 'Online-Direct'
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236307] [nm-device-wifi.c:876] get_active_ap():   Pass #1 
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236356] [nm-device-wifi.c:892] get_active_ap():     AP: 'hpsetup'  36:22:64:d7:6b:1f
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236381] [nm-device-wifi.c:900] get_active_ap():       BSSID mismatch
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236410] [nm-device-wifi.c:892] get_active_ap():     AP: 'BWR Wireless'  00:0c:42:31:a7:00
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236435] [nm-device-wifi.c:900] get_active_ap():       BSSID mismatch
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236464] [nm-device-wifi.c:892] get_active_ap():     AP: 'Berdou'  00:22:75:45:26:f8
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236487] [nm-device-wifi.c:900] get_active_ap():       BSSID mismatch
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236517] [nm-device-wifi.c:892] get_active_ap():     AP: 'AIGS'  c0:3f:0e:82:78:b7
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236544] [nm-device-wifi.c:900] get_active_ap():       BSSID mismatch
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236577] [nm-device-wifi.c:892] get_active_ap():     AP: 'NETGEAR'  e0:46:9a:77:07:24
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236602] [nm-device-wifi.c:900] get_active_ap():       BSSID mismatch
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236631] [nm-device-wifi.c:892] get_active_ap():     AP: 'Online-Direct'  00:02:6f:af:97:20
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236849] [nm-device-wifi.c:932] get_active_ap():       matched
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236920] [nm-device-wifi.c:330] wireless_qual_to_percent(): QL: qual 70/70/0x46, level -38/218/0xDA, noise 0/0/0x0, updated: 0x4B  ** MAX: qual 70/70/0x46, level -110/146/0x92, noise 0/0/0x0, updated: 0x4B
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236957] [nm-device-wifi.c:390] wireless_qual_to_percent(): QL2: level_percent is 100.  max_level 146, level 146.
Oct 27 12:53:06 robertk-laptop NetworkManager[1139]: <debug> [1319712786.236981] [nm-device-wifi.c:400] wireless_qual_to_percent(): QL: Final quality percent is 100 (100).
Oct 27 12:53:06 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>*ERINFO: 1,2,0<CR><LF>'
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): --> 'AT*ENAP?<CR>'
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>*ENAP:0,""<CR><LF>'
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <debug> [mm-at-serial-port.c:298] debug_log(): (ttyACM0): <-- '<CR><LF>*E2NAP: 0,29<CR><LF>'
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <debug> [mm-modem-mbm.c:700] mbm_e2nap_received(): disconnected
Oct 27 12:53:07 robertk-laptop modem-manager[4580]: <info>  [mm-modem.c:742] mm_modem_set_state(): Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> registered)
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <warn> GSM connection failed: (32) Busy
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <info> (wwan0): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <warn> Activation (wwan0) failed.
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418669] [nm-device.c:3663] failed_to_disconnected(): (wwan0): running failed->disconnected transition
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <info> (wwan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <info> (wwan0): deactivating device (reason 'none') [0]
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418826] [nm-system.c:1121] nm_system_iface_flush_routes(): (wwan0): flushing routes ifindex 3 family INET (2)
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418937] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 0.0.0.0/0
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418949] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.0/24
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418959] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.0/24
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418968] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 169.254.0.0/16
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418977] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418987] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.418996] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.91/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419005] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.108/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419014] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419023] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419032] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419330] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.0/8
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419366] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.1/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419395] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.255.255.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.419700] [nm-system.c:182] sync_addresses(): (wwan0): syncing addresses (family 0)
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420100] [nm-system.c:1121] nm_system_iface_flush_routes(): (wwan0): flushing routes ifindex 3 family INET (2)
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420501] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 0.0.0.0/0
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420547] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.0/24
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420580] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.0/24
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420611] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 169.254.0.0/16
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420641] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.420671] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421042] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.91/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421083] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.108/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421116] [nm-netlink-utils.c:317] dump_route():   route idx 2 family INET (2) addr 10.24.7.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421145] [nm-netlink-utils.c:317] dump_route():   route idx 4 family INET (2) addr 10.24.7.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421174] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.0/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421204] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.0/8
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421234] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.0.0.1/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421263] [nm-netlink-utils.c:317] dump_route():   route idx 1 family INET (2) addr 127.255.255.255/32
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <debug> [1319712787.421569] [nm-system.c:182] sync_addresses(): (wwan0): syncing addresses (family 2)
Oct 27 12:53:07 robertk-laptop NetworkManager[1139]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.


any ideas?

---

### Post by rob.kennedy.za on 2011-11-04
Can some please assist or guide me to somewhere that can?

---

