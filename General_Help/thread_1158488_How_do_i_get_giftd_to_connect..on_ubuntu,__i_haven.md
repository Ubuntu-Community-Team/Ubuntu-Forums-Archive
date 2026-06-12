---
title: "How do i get giftd to connect..on ubuntu, ? i haven't been able to connect ANY networ"
date: 2009-05-13
forum: General Help
---

### Post by starlypti on 2009-05-13
no networks connected..///node log file looks like..:


giftd.log:


//
[18:14:38] giftd 0.11.8.1 (Aug  5 2008 14:35:39) started
[18:14:38] Plugin OpenFT (0.2.1.6) successfully loaded and initialized
[18:14:38] OpenFT: ft_openft.c:257(openft_start): Booya! OpenFT in the house!
[18:14:38] *** GIFT-WARNING: OpenFT: guessing max_active=600
[18:14:38] OpenFT: ft_node_cache.c:129(read_cache): opening nodes cache from /home/starlypt/.giFT/OpenFT/nodes...
[18:14:38] OpenFT: ft_node_cache.c:152(read_cache): successfully read 112 nodes
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.27.21.254:2145
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 65.27.21.254:2145: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.48.164.172:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 24.48.164.172:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.60.190.223:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 24.60.190.223:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.0.62.249:2145
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 68.0.62.249:2145: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.2.149.35:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 80.2.149.35:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.57.49.254:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 80.57.49.254:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 82.32.236.145:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 82.32.236.145:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.136.127.66:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 69.136.127.66:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 83.233.233.169:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 83.233.233.169:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.228.241.143:1217
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 213.228.241.143:1217: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.43.37.236:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 24.43.37.236:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.12.37.59:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 24.12.37.59:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.68.97.222:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 155.68.97.222:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.163.153.182:1757
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 80.163.153.182:1757: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 206.174.10.181:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 206.174.10.181:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.162.144.198:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 24.162.144.198:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 137.45.155.242:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 213.77.149.103:1889: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 155.47.148.103:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 69.196.255.249:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 132.177.56.63:1215: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 66.62.245.47:2145: costs 4
[18:14:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:14:38] OpenFT: ft_conn.c:522(start_connection): 67.184.241.41:1265: costs 4
[18:14:38] OpenFT: ft_conn.c:642(ft_conn_initial): began 23 connections (remaining weight: 0)
[18:14:38] *** GIFT-ERROR: couldn't load protocol in file /usr/lib/giFT/libGnutella.la: file not found
[18:14:38] Plugin FastTrack (0.8.9) successfully loaded and initialized
[18:14:38] FastTrack: fst_fasttrack.c:652(fst_giftcb_start): starting up
[18:14:38] FastTrack: fst_fasttrack.c:735(fst_giftcb_start): Loaded 862 supernode addresses from nodes file "/home/starlypt/.giFT/FastTrack/nodes"
[18:14:38] FastTrack: fst_fasttrack.c:749(fst_giftcb_start): Loaded 16074 banned ip ranges from "/home/starlypt/.giFT/FastTrack/banlist"
[18:14:38] FastTrack: fst_fasttrack.c:769(fst_giftcb_start): Http server listening on port 1214
[18:14:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 207.229.75.240:2965, load: 50%
[18:14:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.66.116.19:3153, load: 50%
[18:14:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.57.149.155:32656, load: 50%
[18:14:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.34.84.124:3582, load: 50%
[18:14:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.185.203.120:2376, load: 50%
[18:14:38] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:14:38] giFT: giftd.c:744(init_transfer): recovered 0 state transfers
[18:14:38] *** GIFT-WARNING: updating index...
[18:14:38] giFT: share_cache.c:855(share_write_index): entered
[18:14:38] giFT: share_cache.c:562(share_build_index): entered
[18:14:38] giFT: share_cache.c:893(share_write_index): descending root: /home/starlypt/Downloads/Shared...
[18:14:38] giFT: share_cache.c:465(path_traverse): descending /home/starlypt/Downloads/Shared...
[18:14:38] giFT: share_cache.c:1141(share_read_index): entered
[18:14:38] giFT: share_cache.c:562(share_build_index): entered
[18:14:38] OpenFT: ft_share.c:315(openft_share_sync): beginning share sync...
[18:14:38] OpenFT: ft_share.c:315(openft_share_sync): finishing share sync...
[18:14:38] giFT: share_cache.c:1157(share_read_index): total shares: 0 (0.00MB)
[18:14:38] reaped child process 12593
[18:14:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 207.229.75.240:2965
[18:14:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.114.44.6:3669, load: 50%
[18:14:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.66.116.19:3153
[18:14:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.225.59.56:1724, load: 50%
[18:14:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.57.149.155:32656
[18:14:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.226.251.190:3534, load: 50%
[18:14:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.34.84.124:3582
[18:14:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.207.129.82:3116, load: 50%
[18:14:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.185.203.120:2376
[18:14:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.8.33.20:3841, load: 50%
[18:14:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.114.44.6:3669
[18:14:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.122.50.217:1734, load: 50%
[18:14:58] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:15:03] if_event.c:472(if_event_attach): 127.0.0.1
[18:15:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.225.59.56:1724
[18:15:08] FastTrack: fst_fasttrack.c:150(fst_plugin_connect_next): not connecting to banned supernode 38.117.6.186:3639
[18:15:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.11.98.72:3685, load: 50%
[18:15:08] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:15:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.226.251.190:3534
[18:15:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.194.197.161:1388, load: 50%
[18:15:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.207.129.82:3116
[18:15:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.166.68.122:1214, load: 50%
[18:15:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.8.33.20:3841
[18:15:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.150.145.116:2446, load: 50%
[18:15:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.122.50.217:1734
[18:15:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.24.45.254:3205, load: 50%
[18:15:18] if_event.c:472(if_event_attach): 127.0.0.1
[18:15:18] giFT: daemon.c:482(dcmd_share): entered
[18:15:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.11.98.72:3685
[18:15:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.188.204.16:1214, load: 50%
[18:15:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.194.197.161:1388
[18:15:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.252.48.53:1476, load: 50%
[18:15:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.166.68.122:1214
[18:15:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 142.59.81.149:2462, load: 50%
[18:15:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.150.145.116:2446
[18:15:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.148.26.77:1668, load: 50%
[18:15:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.24.45.254:3205
[18:15:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.255.130.173:1350, load: 50%
[18:15:28] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:15:29] if_event.c:478(if_event_detach): 127.0.0.1
[18:15:38] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:15:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.188.204.16:1214
[18:15:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.128.175.72:1214, load: 50%
[18:15:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.252.48.53:1476
[18:15:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 204.251.85.37:3028, load: 50%
[18:15:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 142.59.81.149:2462
[18:15:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.200.92.106:3958, load: 50%
[18:15:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.148.26.77:1668
[18:15:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.68.140.108:2803, load: 50%
[18:15:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.255.130.173:1350
[18:15:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.164.155.155:2275, load: 50%
[18:15:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 204.251.85.37:3028
[18:15:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.97.153.24:3516, load: 50%
[18:15:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.97.153.24:3516
[18:15:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.1.220.196:3233, load: 50%
[18:15:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.128.175.72:1214
[18:15:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.204.216.249:1933, load: 50%
[18:15:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.200.92.106:3958
[18:15:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.196.11.170:1437, load: 50%
[18:15:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.68.140.108:2803
[18:15:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 207.81.93.244:3738, load: 50%
[18:15:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.164.155.155:2275
[18:15:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 70.179.187.233:1152, load: 50%
[18:15:58] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:16:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.1.220.196:3233
[18:16:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.41.26.128:3583, load: 50%
[18:16:03] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:16:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.204.216.249:1933
[18:16:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.118.7.45:1214, load: 50%
[18:16:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.196.11.170:1437
[18:16:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.198.6.236:1214, load: 50%
[18:16:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 207.81.93.244:3738
[18:16:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.119.170.84:1902, load: 50%
[18:16:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.119.170.84:1902
[18:16:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.32.206.117:1721, load: 50%
[18:16:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.118.7.45:1214
[18:16:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.23.124.122:32656, load: 50%
[18:16:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 70.179.187.233:1152
[18:16:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.157.105.112:1694, load: 50%
[18:16:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.41.26.128:3583
[18:16:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.193.135.57:3403, load: 50%
[18:16:23] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:16:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.198.6.236:1214
[18:16:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.180.110.130:2025, load: 50%
[18:16:24] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:16:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.32.206.117:1721
[18:16:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.27.121.36:2816, load: 50%
[18:16:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.23.124.122:32656
[18:16:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.77.47.83:1730, load: 50%
[18:16:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.77.47.83:1730
[18:16:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.47.72.100:3182, load: 50%
[18:16:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.157.105.112:1694
[18:16:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.62.52.249:2701, load: 50%
[18:16:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.62.52.249:2701
[18:16:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.87.202.47:3187, load: 50%
[18:16:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.193.135.57:3403
[18:16:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.31.6.35:2408, load: 50%
[18:16:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:16:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 62.202.0.22:1215
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 85.195.68.3:1470
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.97.7.188:1214
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:16:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:16:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.180.110.130:2025
[18:16:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.53.101.215:1214, load: 50%
[18:16:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.27.121.36:2816
[18:16:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.43.51.55:2995, load: 50%
[18:16:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.47.72.100:3182
[18:16:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.53.23.240:1589, load: 50%
[18:16:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.87.202.47:3187
[18:16:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.102.92.144:3788, load: 50%
[18:16:44] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:16:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.31.6.35:2408
[18:16:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.163.110.126:3810, load: 50%
[18:16:48] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:16:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.53.23.240:1589
[18:16:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.236.177.218:3825, load: 50%
[18:16:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.53.101.215:1214
[18:16:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.196.5.5:1940, load: 50%
[18:16:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.43.51.55:2995
[18:16:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.175.174.163:1749, load: 50%
[18:16:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.102.92.144:3788
[18:16:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.224.82.129:1290, load: 50%
[18:17:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.163.110.126:3810
[18:17:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.27.235.136:3772, load: 50%
[18:17:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.236.177.218:3825
[18:17:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.127.42.255:1214, load: 50%
[18:17:08] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:17:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.196.5.5:1940
[18:17:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.137.131.41:3637, load: 50%
[18:17:09] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:17:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.175.174.163:1749
[18:17:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.226.239.193:2143, load: 50%
[18:17:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.224.82.129:1290
[18:17:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.225.112.168:2333, load: 50%
[18:17:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.27.235.136:3772
[18:17:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.173.215.251:2925, load: 50%
[18:17:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.173.215.251:2925
[18:17:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.172.144.250:3910, load: 50%
[18:17:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.127.42.255:1214
[18:17:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.198.28.177:2120, load: 50%
[18:17:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.198.28.177:2120
[18:17:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.239.234.242:1395, load: 50%
[18:17:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.137.131.41:3637
[18:17:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.126.9.121:3517, load: 50%
[18:17:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.226.239.193:2143
[18:17:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.196.102.137:1811, load: 50%
[18:17:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.225.112.168:2333
[18:17:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.193.208.188:3417, load: 50%
[18:17:29] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:17:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.172.144.250:3910
[18:17:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.64.197.111:1278, load: 50%
[18:17:33] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:17:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.239.234.242:1395
[18:17:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 195.241.151.157:1214, load: 50%
[18:17:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.126.9.121:3517
[18:17:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 212.21.240.54:3681, load: 50%
[18:17:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.196.102.137:1811
[18:17:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 200.89.152.224:3023, load: 50%
[18:17:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.193.208.188:3417
[18:17:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.232.253.73:1214, load: 50%
[18:17:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.64.197.111:1278
[18:17:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.232.163.195:2549, load: 50%
[18:17:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 195.241.151.157:1214
[18:17:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.65.102.29:3479, load: 50%
[18:17:53] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:17:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 212.21.240.54:3681
[18:17:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.105.57.224:3513, load: 50%
[18:17:54] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:17:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 200.89.152.224:3023
[18:17:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.37.177.47:1214, load: 50%
[18:17:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.232.253.73:1214
[18:17:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.225.173.112:3410, load: 50%
[18:18:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.232.163.195:2549
[18:18:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.134.22.176:1590, load: 50%
[18:18:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.65.102.29:3479
[18:18:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.245.162.176:1214, load: 50%
[18:18:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.105.57.224:3513
[18:18:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 211.28.228.198:3292, load: 50%
[18:18:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.37.177.47:1214
[18:18:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.236.182.0:1081, load: 50%
[18:18:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.225.173.112:3410
[18:18:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.0.48.181:3106, load: 50%
[18:18:14] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:18:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.134.22.176:1590
[18:18:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.101.250.151:1575, load: 50%
[18:18:18] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:18:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.245.162.176:1214
[18:18:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.67.152.25:1351, load: 50%
[18:18:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 211.28.228.198:3292
[18:18:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.14.34.223:3308, load: 50%
[18:18:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.236.182.0:1081
[18:18:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.230.130.39:1845, load: 50%
[18:18:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.0.48.181:3106
[18:18:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 205.206.198.7:1053, load: 50%
[18:18:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.101.250.151:1575
[18:18:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.20.204.50:1848, load: 50%
[18:18:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.67.152.25:1351
[18:18:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.8.203.208:3432, load: 50%
[18:18:38] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:18:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:18:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.97.7.188:1214
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 85.195.68.3:1470
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 62.202.0.22:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.162.144.198:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.12.37.59:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 83.233.233.169:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.136.127.66:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 82.32.236.145:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.57.49.254:1215
[18:18:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.2.149.35:1215
[18:18:38] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:18:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.14.34.223:3308
[18:18:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.30.5.214:1486, load: 50%
[18:18:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.230.130.39:1845
[18:18:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.222.92.106:32656, load: 50%
[18:18:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 205.206.198.7:1053
[18:18:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.150.86.116:1219, load: 50%
[18:18:42] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.222.92.106:32656
[18:18:42] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.163.150.171:2415, load: 50%
[18:18:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.20.204.50:1848
[18:18:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 217.217.33.96:3746, load: 50%
[18:18:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.8.203.208:3432
[18:18:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 129.11.217.230:3635, load: 50%
[18:18:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.30.5.214:1486
[18:18:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.179.157.214:1551, load: 50%
[18:18:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.150.86.116:1219
[18:18:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.86.47.85:1157, load: 50%
[18:18:57] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.163.150.171:2415
[18:18:57] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.13.178.206:2841, load: 50%
[18:18:59] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:19:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.217.33.96:3746
[18:19:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.160.73.165:3546, load: 50%
[18:19:03] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:19:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 129.11.217.230:3635
[18:19:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.150.171.122:1220, load: 50%
[18:19:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.179.157.214:1551
[18:19:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.67.22.116:3772, load: 50%
[18:19:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.86.47.85:1157
[18:19:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.57.24.129:3947, load: 50%
[18:19:12] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.13.178.206:2841
[18:19:12] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.98.4.232:2748, load: 50%
[18:19:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.160.73.165:3546
[18:19:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.16.215.27:1084, load: 50%
[18:19:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.150.171.122:1220
[18:19:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.51.193.33:3856, load: 50%
[18:19:23] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:19:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.67.22.116:3772
[18:19:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.82.18.189:1079, load: 50%
[18:19:24] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:19:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.57.24.129:3947
[18:19:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.11.90.193:2251, load: 50%
[18:19:27] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.98.4.232:2748
[18:19:27] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.0.151.40:1494, load: 50%
[18:19:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.16.215.27:1084
[18:19:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.181.166.229:1350, load: 50%
[18:19:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.51.193.33:3856
[18:19:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.200.16.169:3228, load: 50%
[18:19:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.200.16.169:3228
[18:19:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.166.50.98:3417, load: 50%
[18:19:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.82.18.189:1079
[18:19:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.225.37.63:2228, load: 50%
[18:19:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.11.90.193:2251
[18:19:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.57.9.252:2740, load: 50%
[18:19:42] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.0.151.40:1494
[18:19:42] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.34.225.245:1211, load: 50%
[18:19:44] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:19:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.181.166.229:1350
[18:19:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.224.171.146:1966, load: 50%
[18:19:48] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:19:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.166.50.98:3417
[18:19:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.38.212.149:3010, load: 50%
[18:19:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.38.212.149:3010
[18:19:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.58.52.69:2128, load: 50%
[18:19:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.225.37.63:2228
[18:19:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.211.91.99:3215, load: 50%
[18:19:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.57.9.252:2740
[18:19:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.179.61.67:1859, load: 50%
[18:19:57] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.34.225.245:1211
[18:19:57] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.8.180.205:1721, load: 50%
[18:20:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.224.171.146:1966
[18:20:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.233.25.9:1816, load: 50%
[18:20:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.233.25.9:1816
[18:20:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.202.198.94:1385, load: 50%
[18:20:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.58.52.69:2128
[18:20:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.205.123.92:3627, load: 50%
[18:20:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.205.123.92:3627
[18:20:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.50.35.154:3658, load: 50%
[18:20:08] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:20:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.211.91.99:3215
[18:20:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.36.34.207:1985, load: 50%
[18:20:09] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:20:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.179.61.67:1859
[18:20:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.127.89.203:3336, load: 50%
[18:20:12] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.8.180.205:1721
[18:20:12] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.25.61.28:3960, load: 50%
[18:20:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.202.198.94:1385
[18:20:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.0.23.95:2523, load: 50%
[18:20:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.50.35.154:3658
[18:20:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.215.203.191:1794, load: 50%
[18:20:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.36.34.207:1985
[18:20:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.228.60.88:3142, load: 50%
[18:20:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.127.89.203:3336
[18:20:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 205.206.108.192:1095, load: 50%
[18:20:27] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.25.61.28:3960
[18:20:27] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.60.70.180:1719, load: 50%
[18:20:29] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:20:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.0.23.95:2523
[18:20:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.235.131.254:2151, load: 50%
[18:20:33] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:20:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.215.203.191:1794
[18:20:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.44.129.167:2732, load: 50%
[18:20:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:20:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.0.62.249:2145
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.60.190.223:1215
[18:20:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.48.164.172:1215
[18:20:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.228.60.88:3142
[18:20:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.49.100.102:2141, load: 50%
[18:20:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 205.206.108.192:1095
[18:20:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.82.94.142:3068, load: 50%
[18:20:42] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.60.70.180:1719
[18:20:42] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.132.156.225:2991, load: 50%
[18:20:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.235.131.254:2151
[18:20:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.174.0.86:3112, load: 50%
[18:20:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.44.129.167:2732
[18:20:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.161.166.58:1214, load: 50%
[18:20:53] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:20:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.49.100.102:2141
[18:20:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.191.224.218:1094, load: 50%
[18:20:54] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:20:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.82.94.142:3068
[18:20:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.150.187.251:1573, load: 50%
[18:20:57] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.132.156.225:2991
[18:20:57] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.31.171.72:1129, load: 50%
[18:21:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.174.0.86:3112
[18:21:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.161.59.11:1175, load: 50%
[18:21:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.161.166.58:1214
[18:21:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 210.14.27.58:1214, load: 50%
[18:21:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 210.14.27.58:1214
[18:21:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.195.247.50:3840, load: 50%
[18:21:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.191.224.218:1094
[18:21:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.225.120.138:3060, load: 50%
[18:21:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.150.187.251:1573
[18:21:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.30.88.73:2301, load: 50%
[18:21:12] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.31.171.72:1129
[18:21:12] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.153.25.89:3387, load: 50%
[18:21:14] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:21:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.161.59.11:1175
[18:21:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.101.211.121:3667, load: 50%
[18:21:18] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:21:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.195.247.50:3840
[18:21:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.195.232.24:32656, load: 50%
[18:21:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.225.120.138:3060
[18:21:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.8.77.67:1881, load: 50%
[18:21:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.30.88.73:2301
[18:21:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.165.186.227:3326, load: 50%
[18:21:27] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.153.25.89:3387
[18:21:27] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.67.248.123:2528, load: 50%
[18:21:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.67.248.123:2528
[18:21:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.57.74.57:3343, load: 50%
[18:21:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.101.211.121:3667
[18:21:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.232.15.82:2306, load: 50%
[18:21:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.195.232.24:32656
[18:21:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.33.160.106:3407, load: 50%
[18:21:37] if_event.c:472(if_event_attach): 127.0.0.1
[18:21:37] giFT: daemon.c:482(dcmd_share): entered
[18:21:37] giFT: daemon.c:482(dcmd_share): entered
[18:21:38] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:21:39] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:21:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.8.77.67:1881
[18:21:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.49.200.41:3270, load: 50%
[18:21:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.165.186.227:3326
[18:21:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.10.207.190:1205, load: 50%
[18:21:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.57.74.57:3343
[18:21:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.175.160.196:1524, load: 50%
[18:21:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.232.15.82:2306
[18:21:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.26.176.185:3466, load: 50%
[18:21:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.26.176.185:3466
[18:21:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.3.3.16:2405, load: 50%
[18:21:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.33.160.106:3407
[18:21:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.67.52.77:1906, load: 50%
[18:21:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.49.200.41:3270
[18:21:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.184.255.47:2889, load: 50%
[18:21:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.10.207.190:1205
[18:21:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.96.66.205:1435, load: 50%
[18:21:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.175.160.196:1524
[18:21:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.141.167.188:1287, load: 50%
[18:21:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.141.167.188:1287
[18:21:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.26.78.195:2761, load: 50%
[18:21:59] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:22:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.3.3.16:2405
[18:22:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.111.251.227:2931, load: 50%
[18:22:03] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:22:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.67.52.77:1906
[18:22:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.37.94.95:1214, load: 50%
[18:22:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.184.255.47:2889
[18:22:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 200.89.130.248:3970, load: 50%
[18:22:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.96.66.205:1435
[18:22:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.131.145.33:1085, load: 50%
[18:22:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.26.78.195:2761
[18:22:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.93.146.145:32656, load: 50%
[18:22:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.111.251.227:2931
[18:22:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 70.112.1.158:3500, load: 50%
[18:22:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 70.112.1.158:3500
[18:22:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.52.11.194:3057, load: 50%
[18:22:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.37.94.95:1214
[18:22:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.111.128.216:2307, load: 50%
[18:22:23] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:22:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 200.89.130.248:3970
[18:22:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.171.35.245:3336, load: 50%
[18:22:24] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:22:25] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.131.145.33:1085
[18:22:25] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.61.53.9:2961, load: 50%
[18:22:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.93.146.145:32656
[18:22:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 134.129.52.156:1214, load: 50%
[18:22:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.52.11.194:3057
[18:22:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 220.72.230.221:1899, load: 50%
[18:22:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.111.128.216:2307
[18:22:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.195.107.105:2818, load: 50%
[18:22:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.195.107.105:2818
[18:22:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.83.76.236:1665, load: 50%
[18:22:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:22:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.97.7.188:1214
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 85.195.68.3:1470
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 62.202.0.22:1215
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.68.97.222:1215
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.163.153.182:1757
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 206.174.10.181:1215
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.43.37.236:1215
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.228.241.143:1217
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.27.21.254:2145
[18:22:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 81.106.110.3:1215
[18:22:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.171.35.245:3336
[18:22:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.109.23.129:2227, load: 50%
[18:22:40] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.61.53.9:2961
[18:22:40] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.80.150.210:1230, load: 50%
[18:22:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 134.129.52.156:1214
[18:22:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.175.225.26:3927, load: 50%
[18:22:44] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:22:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 220.72.230.221:1899
[18:22:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.175.62.53:2042, load: 50%
[18:22:48] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:22:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.83.76.236:1665
[18:22:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.56.8.3:1226, load: 50%
[18:22:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.109.23.129:2227
[18:22:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 217.209.35.69:3084, load: 50%
[18:22:55] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.80.150.210:1230
[18:22:55] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.224.165.188:1200, load: 50%
[18:22:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.175.225.26:3927
[18:22:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.58.81.86:2801, load: 50%
[18:23:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.175.62.53:2042
[18:23:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.28.135.229:3330, load: 50%
[18:23:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.28.135.229:3330
[18:23:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.230.185.9:3499, load: 50%
[18:23:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.56.8.3:1226
[18:23:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.9.198.47:2874, load: 50%
[18:23:08] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:23:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.209.35.69:3084
[18:23:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 198.166.58.196:1275, load: 50%
[18:23:09] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:23:10] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.224.165.188:1200
[18:23:10] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.112.190.46:2356, load: 50%
[18:23:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.58.81.86:2801
[18:23:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.62.103.42:2225, load: 50%
[18:23:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.230.185.9:3499
[18:23:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.37.239.44:3435, load: 50%
[18:23:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.9.198.47:2874
[18:23:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.83.226.140:1200, load: 50%
[18:23:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.112.190.46:2356
[18:23:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.198.150.120:2445, load: 50%
[18:23:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 198.166.58.196:1275
[18:23:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.23.174.79:2350, load: 50%
[18:23:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.62.103.42:2225
[18:23:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.243.115.23:2638, load: 50%
[18:23:29] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:23:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.37.239.44:3435
[18:23:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.230.170.88:1858, load: 50%
[18:23:33] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:23:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.83.226.140:1200
[18:23:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.106.62.45:3819, load: 50%
[18:23:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.198.150.120:2445
[18:23:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.106.160.150:2537, load: 50%
[18:23:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.23.174.79:2350
[18:23:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.190.183.161:2815, load: 50%
[18:23:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.243.115.23:2638
[18:23:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 194.249.30.236:3026, load: 50%
[18:23:48] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.230.170.88:1858
[18:23:48] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.46.138.159:3483, load: 50%
[18:23:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.106.62.45:3819
[18:23:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.29.121.164:3748, load: 50%
[18:23:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.106.160.150:2537
[18:23:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.86.200.231:2351, load: 50%
[18:23:53] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:23:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.190.183.161:2815
[18:23:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.104.73.110:2560, load: 50%
[18:23:54] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:23:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 194.249.30.236:3026
[18:23:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.227.112.76:3869, load: 50%
[18:24:03] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.46.138.159:3483
[18:24:03] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.71.60.187:1318, load: 50%
[18:24:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.29.121.164:3748
[18:24:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 217.162.207.246:2268, load: 50%
[18:24:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.86.200.231:2351
[18:24:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.162.221.140:1677, load: 50%
[18:24:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.162.207.246:2268
[18:24:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.141.97.160:2526, load: 50%
[18:24:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.162.221.140:1677
[18:24:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.84.158.234:3567, load: 50%
[18:24:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.104.73.110:2560
[18:24:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.83.34.177:1519, load: 50%
[18:24:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.227.112.76:3869
[18:24:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.72.92.228:3514, load: 50%
[18:24:14] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:24:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.71.60.187:1318
[18:24:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.168.191.26:1126, load: 50%
[18:24:18] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:24:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.141.97.160:2526
[18:24:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.77.80.20:32656, load: 50%
[18:24:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.84.158.234:3567
[18:24:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.136.204.63:2353, load: 50%
[18:24:22] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.77.80.20:32656
[18:24:22] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.141.142.90:3588, load: 50%
[18:24:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.83.34.177:1519
[18:24:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.56.161.179:32656, load: 50%
[18:24:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.72.92.228:3514
[18:24:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.137.131.82:1214, load: 50%
[18:24:33] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.168.191.26:1126
[18:24:33] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.189.165.223:1603, load: 50%
[18:24:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.189.165.223:1603
[18:24:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 217.217.1.103:1171, load: 50%
[18:24:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.136.204.63:2353
[18:24:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.67.86.151:2069, load: 50%
[18:24:37] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.141.142.90:3588
[18:24:37] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.22.6.18:2858, load: 50%
[18:24:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:24:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.48.164.172:1215
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.60.190.223:1215
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.0.62.249:2145
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:24:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:24:38] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:24:39] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:24:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.56.161.179:32656
[18:24:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.11.121.95:32656, load: 50%
[18:24:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.137.131.82:1214
[18:24:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.137.134.22:1624, load: 50%
[18:24:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.217.1.103:1171
[18:24:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.56.33.123:3211, load: 50%
[18:24:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.56.33.123:3211
[18:24:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.102.205.243:1074, load: 50%
[18:24:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.67.86.151:2069
[18:24:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.212.150.190:3507, load: 50%
[18:24:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.22.6.18:2858
[18:24:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.101.219.233:2847, load: 50%
[18:24:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.11.121.95:32656
[18:24:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.11.21.88:1090, load: 50%
[18:24:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.137.134.22:1624
[18:24:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.30.16.172:1543, load: 50%
[18:24:59] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:25:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.102.205.243:1074
[18:25:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.3.233.113:3558, load: 50%
[18:25:04] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:25:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.212.150.190:3507
[18:25:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.193.235.40:1214, load: 50%
[18:25:07] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.101.219.233:2847
[18:25:07] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.161.32.190:2675, load: 50%
[18:25:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.11.21.88:1090
[18:25:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 205.206.85.29:3269, load: 50%
[18:25:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.30.16.172:1543
[18:25:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.15.30.50:3499, load: 50%
[18:25:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.15.30.50:3499
[18:25:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.2.179.47:2968, load: 50%
[18:25:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.3.233.113:3558
[18:25:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.69.214.139:2452, load: 50%
[18:25:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.193.235.40:1214
[18:25:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.232.201.46:3969, load: 50%
[18:25:22] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.161.32.190:2675
[18:25:22] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.47.196.222:2611, load: 50%
[18:25:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 205.206.85.29:3269
[18:25:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.226.46.139:32656, load: 50%
[18:25:24] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:25:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.2.179.47:2968
[18:25:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.224.80.211:2085, load: 50%
[18:25:28] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:25:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.69.214.139:2452
[18:25:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.117.185.242:2349, load: 50%
[18:25:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.232.201.46:3969
[18:25:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 154.20.27.62:32656, load: 50%
[18:25:37] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.47.196.222:2611
[18:25:37] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.77.15.156:3472, load: 50%
[18:25:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.226.46.139:32656
[18:25:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.182.104.154:2202, load: 50%
[18:25:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.224.80.211:2085
[18:25:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.202.70.191:3207, load: 50%
[18:25:48] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:25:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.117.185.242:2349
[18:25:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.27.230.84:1643, load: 50%
[18:25:49] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:25:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 154.20.27.62:32656
[18:25:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.18.219.202:3069, load: 50%
[18:25:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.18.219.202:3069
[18:25:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.100.47.192:3374, load: 50%
[18:25:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.77.15.156:3472
[18:25:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.170.88.100:1750, load: 50%
[18:25:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.170.88.100:1750
[18:25:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.118.24.129:3626, load: 50%
[18:25:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.118.24.129:3626
[18:25:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.3.208.110:2045, load: 50%
[18:25:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.182.104.154:2202
[18:25:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.188.188.130:1634, load: 50%
[18:25:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.202.70.191:3207
[18:25:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.176.246.52:3086, load: 50%
[18:26:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.27.230.84:1643
[18:26:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.55.161.11:2430, load: 50%
[18:26:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.55.161.11:2430
[18:26:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.143.225.240:2279, load: 50%
[18:26:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.100.47.192:3374
[18:26:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.236.147.46:3209, load: 50%
[18:26:07] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.3.208.110:2045
[18:26:07] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.195.90.68:1227, load: 50%
[18:26:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.195.90.68:1227
[18:26:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 168.131.25.222:3026, load: 50%
[18:26:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.188.188.130:1634
[18:26:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.12.58.22:2739, load: 50%
[18:26:09] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:26:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.176.246.52:3086
[18:26:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.76.53.147:3445, load: 50%
[18:26:13] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:26:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.143.225.240:2279
[18:26:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.28.8.100:2467, load: 50%
[18:26:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.236.147.46:3209
[18:26:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.84.138.199:2356, load: 50%
[18:26:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 168.131.25.222:3026
[18:26:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.222.50.156:2455, load: 50%
[18:26:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.12.58.22:2739
[18:26:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.26.227.62:1828, load: 50%
[18:26:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.76.53.147:3445
[18:26:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.194.97.49:1214, load: 50%
[18:26:33] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:26:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.28.8.100:2467
[18:26:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 203.247.199.131:2643, load: 50%
[18:26:34] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:26:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.84.138.199:2356
[18:26:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.27.214.232:1052, load: 50%
[18:26:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.27.214.232:1052
[18:26:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.80.75.165:3587, load: 50%
[18:26:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.222.50.156:2455
[18:26:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 82.81.192.229:1485, load: 50%
[18:26:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:26:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 85.195.68.3:1470
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.43.37.236:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.228.241.143:1217
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 65.27.21.254:2145
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.2.149.35:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 80.57.49.254:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 82.32.236.145:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.136.127.66:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 83.233.233.169:1215
[18:26:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.12.37.59:1215
[18:26:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.26.227.62:1828
[18:26:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.24.173.115:2429, load: 50%
[18:26:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.194.97.49:1214
[18:26:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.49.47.161:3941, load: 50%
[18:26:49] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 203.247.199.131:2643
[18:26:49] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.1.199.10:1097, load: 50%
[18:26:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.80.75.165:3587
[18:26:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 216.167.225.52:1454, load: 50%
[18:26:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 82.81.192.229:1485
[18:26:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.59.25.131:2671, load: 50%
[18:26:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.24.173.115:2429
[18:26:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.41.191.40:1344, load: 50%
[18:26:54] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:26:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.49.47.161:3941
[18:26:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.1.24.188:3789, load: 50%
[18:26:58] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:27:04] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.1.199.10:1097
[18:27:04] FastTrack: fst_session.c:128(fst_session_connect): connecting to 212.127.196.165:3669, load: 50%
[18:27:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 216.167.225.52:1454
[18:27:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.124.101.132:2192, load: 50%
[18:27:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.59.25.131:2671
[18:27:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.222.45.34:1145, load: 50%
[18:27:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.41.191.40:1344
[18:27:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.179.76.76:3535, load: 50%
[18:27:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.1.24.188:3789
[18:27:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.218.54.99:2405, load: 50%
[18:27:18] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:27:19] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 212.127.196.165:3669
[18:27:19] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.156.162.155:1908, load: 50%
[18:27:19] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:27:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.124.101.132:2192
[18:27:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 212.10.223.227:3819, load: 50%
[18:27:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.222.45.34:1145
[18:27:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.10.191.9:2295, load: 50%
[18:27:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.179.76.76:3535
[18:27:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.111.73.127:3359, load: 50%
[18:27:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.218.54.99:2405
[18:27:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.187.18.210:1992, load: 50%
[18:27:34] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.156.162.155:1908
[18:27:34] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.131.173.95:1102, load: 50%
[18:27:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.131.173.95:1102
[18:27:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.65.140.246:3856, load: 50%
[18:27:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 212.10.223.227:3819
[18:27:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.118.0.115:2874, load: 50%
[18:27:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.10.191.9:2295
[18:27:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.0.161.166:1386, load: 50%
[18:27:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.111.73.127:3359
[18:27:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.20.140.226:2891, load: 50%
[18:27:39] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:27:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.187.18.210:1992
[18:27:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.33.127.241:2145, load: 50%
[18:27:43] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:27:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.65.140.246:3856
[18:27:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.179.238.166:3233, load: 50%
[18:27:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.118.0.115:2874
[18:27:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.227.20.147:2021, load: 50%
[18:27:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.0.161.166:1386
[18:27:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.107.129.199:1295, load: 50%
[18:27:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.20.140.226:2891
[18:27:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.195.153.222:3525, load: 50%
[18:27:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.33.127.241:2145
[18:27:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 211.157.101.97:1989, load: 50%
[18:28:03] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:28:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.179.238.166:3233
[18:28:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.1.186.156:1122, load: 50%
[18:28:05] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:28:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.227.20.147:2021
[18:28:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.42.107.22:2735, load: 50%
[18:28:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.107.129.199:1295
[18:28:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.89.123.200:3150, load: 50%
[18:28:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.195.153.222:3525
[18:28:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.85.114.109:1271, load: 50%
[18:28:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 211.157.101.97:1989
[18:28:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.192.72.28:1722, load: 50%
[18:28:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.1.186.156:1122
[18:28:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.226.225.50:1186, load: 50%
[18:28:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.42.107.22:2735
[18:28:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 216.232.191.61:2621, load: 50%
[18:28:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 216.232.191.61:2621
[18:28:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.205.137.48:1250, load: 50%
[18:28:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.89.123.200:3150
[18:28:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.195.192.249:2742, load: 50%
[18:28:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.85.114.109:1271
[18:28:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 80.222.196.4:3786, load: 50%
[18:28:25] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:28:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.192.72.28:1722
[18:28:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.100.194.158:2566, load: 50%
[18:28:28] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:28:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.226.225.50:1186
[18:28:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.67.31.95:2148, load: 50%
[18:28:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.205.137.48:1250
[18:28:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.62.40.121:2783, load: 50%
[18:28:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.195.192.249:2742
[18:28:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.218.198.208:2551, load: 50%
[18:28:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:28:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.0.62.249:2145
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.60.190.223:1215
[18:28:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.48.164.172:1215
[18:28:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 80.222.196.4:3786
[18:28:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.190.201.196:3359, load: 50%
[18:28:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.100.194.158:2566
[18:28:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.57.149.123:1667, load: 50%
[18:28:48] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:28:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.67.31.95:2148
[18:28:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.166.79.102:1694, load: 50%
[18:28:50] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:28:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.166.79.102:1694
[18:28:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.31.184.75:2453, load: 50%
[18:28:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.62.40.121:2783
[18:28:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.73.176.140:3221, load: 50%
[18:28:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.218.198.208:2551
[18:28:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.112.18.164:2935, load: 50%
[18:28:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.190.201.196:3359
[18:28:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.109.47.87:1700, load: 50%
[18:28:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.57.149.123:1667
[18:28:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.164.212.235:1690, load: 50%
[18:29:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.31.184.75:2453
[18:29:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.171.16.148:32656, load: 50%
[18:29:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.73.176.140:3221
[18:29:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 209.89.246.175:1402, load: 50%
[18:29:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.112.18.164:2935
[18:29:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.254.2.125:3902, load: 50%
[18:29:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.109.47.87:1700
[18:29:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.168.113.206:1214, load: 50%
[18:29:10] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:29:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.164.212.235:1690
[18:29:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.129.66.129:2130, load: 50%
[18:29:13] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:29:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.171.16.148:32656
[18:29:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.109.123.237:1100, load: 50%
[18:29:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 209.89.246.175:1402
[18:29:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.228.157.192:2976, load: 50%
[18:29:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.254.2.125:3902
[18:29:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.147.9.124:3447, load: 50%
[18:29:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.168.113.206:1214
[18:29:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.156.81.178:3712, load: 50%
[18:29:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.129.66.129:2130
[18:29:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.141.223.98:2376, load: 50%
[18:29:33] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:29:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.109.123.237:1100
[18:29:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.224.234.231:32656, load: 50%
[18:29:35] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:29:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.228.157.192:2976
[18:29:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.39.16.106:1214, load: 50%
[18:29:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.147.9.124:3447
[18:29:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.118.55.75:1391, load: 50%
[18:29:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.156.81.178:3712
[18:29:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.29.170.116:3909, load: 50%
[18:29:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.141.223.98:2376
[18:29:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.80.46.194:3310, load: 50%
[18:29:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.224.234.231:32656
[18:29:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.81.233.202:1109, load: 50%
[18:29:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.39.16.106:1214
[18:29:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.217.6.177:2132, load: 50%
[18:29:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.118.55.75:1391
[18:29:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.142.83.12:3631, load: 50%
[18:29:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.29.170.116:3909
[18:29:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.234.27.241:3710, load: 50%
[18:29:55] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:29:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.80.46.194:3310
[18:29:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.157.132.223:1764, load: 50%
[18:29:58] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:30:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.81.233.202:1109
[18:30:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.23.98.124:1328, load: 50%
[18:30:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.217.6.177:2132
[18:30:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.65.2.19:2106, load: 50%
[18:30:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.142.83.12:3631
[18:30:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.91.130.122:1552, load: 50%
[18:30:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.234.27.241:3710
[18:30:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.34.220.90:3464, load: 50%
[18:30:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.157.132.223:1764
[18:30:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.126.60.169:2681, load: 50%
[18:30:18] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:30:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.23.98.124:1328
[18:30:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.37.252.252:1859, load: 50%
[18:30:20] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:30:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.65.2.19:2106
[18:30:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.195.122.250:2284, load: 50%
[18:30:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.91.130.122:1552
[18:30:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 70.25.67.178:1884, load: 50%
[18:30:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.34.220.90:3464
[18:30:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 220.126.21.125:2414, load: 50%
[18:30:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.126.60.169:2681
[18:30:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.187.113.90:2438, load: 50%
[18:30:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.37.252.252:1859
[18:30:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.101.0.2:2633, load: 50%
[18:30:36] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.195.122.250:2284
[18:30:36] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.45.111.5:2438, load: 50%
[18:30:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 70.25.67.178:1884
[18:30:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.9.41.45:3709, load: 50%
[18:30:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:30:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 62.202.0.22:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 206.174.10.181:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.162.144.198:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 82.44.103.30:2145
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.226.75.133:2050
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.16.234.37:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 62.238.10.251:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.197.198.9:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 217.125.1.231:1215
[18:30:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 198.53.195.39:1215
[18:30:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 220.126.21.125:2414
[18:30:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.194.239.203:2532, load: 50%
[18:30:40] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:30:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.187.113.90:2438
[18:30:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.148.141.153:3342, load: 50%
[18:30:43] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:30:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.101.0.2:2633
[18:30:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 136.165.82.246:2176, load: 50%
[18:30:51] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.45.111.5:2438
[18:30:51] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.193.155.232:1493, load: 50%
[18:30:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.9.41.45:3709
[18:30:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.254.51.125:2090, load: 50%
[18:30:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.194.239.203:2532
[18:30:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.141.0.131:2106, load: 50%
[18:30:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.148.141.153:3342
[18:30:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 199.212.74.189:3888, load: 50%
[18:31:03] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:31:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 136.165.82.246:2176
[18:31:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.171.165.172:2806, load: 50%
[18:31:05] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:31:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.171.165.172:2806
[18:31:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.84.64.29:2981, load: 50%
[18:31:06] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.193.155.232:1493
[18:31:06] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.108.112.76:2341, load: 50%
[18:31:07] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.108.112.76:2341
[18:31:07] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.101.120.15:1493, load: 50%
[18:31:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.254.51.125:2090
[18:31:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.211.107.212:1589, load: 50%
[18:31:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.141.0.131:2106
[18:31:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.91.27.45:2017, load: 50%
[18:31:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 199.212.74.189:3888
[18:31:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.222.34.105:3338, load: 50%
[18:31:13] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.222.34.105:3338
[18:31:13] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.185.85.214:1567, load: 50%
[18:31:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.84.64.29:2981
[18:31:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.202.229.53:3865, load: 50%
[18:31:22] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.101.120.15:1493
[18:31:22] FastTrack: fst_session.c:128(fst_session_connect): connecting to 137.186.166.59:3120, load: 50%
[18:31:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.211.107.212:1589
[18:31:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.215.67.55:2071, load: 50%
[18:31:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.91.27.45:2017
[18:31:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.137.71.20:1561, load: 50%
[18:31:25] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:31:28] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.185.85.214:1567
[18:31:28] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.228.28.116:1950, load: 50%
[18:31:28] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:31:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.202.229.53:3865
[18:31:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.203.233.11:2439, load: 50%
[18:31:37] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 137.186.166.59:3120
[18:31:37] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.148.40.95:1282, load: 50%
[18:31:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.215.67.55:2071
[18:31:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 157.158.56.66:3114, load: 50%
[18:31:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.137.71.20:1561
[18:31:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.222.22.120:1787, load: 50%
[18:31:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 157.158.56.66:3114
[18:31:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.15.195.99:2630, load: 50%
[18:31:43] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.228.28.116:1950
[18:31:43] FastTrack: fst_session.c:128(fst_session_connect): connecting to 130.236.194.97:2646, load: 50%
[18:31:48] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:31:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.203.233.11:2439
[18:31:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 213.84.164.177:3380, load: 50%
[18:31:50] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:31:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.148.40.95:1282
[18:31:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.53.247.84:1214, load: 50%
[18:31:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.222.22.120:1787
[18:31:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.194.208.245:1825, load: 50%
[18:31:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.194.208.245:1825
[18:31:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 220.237.15.177:3703, load: 50%
[18:31:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.15.195.99:2630
[18:31:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 12.215.126.240:3386, load: 50%
[18:31:58] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 130.236.194.97:2646
[18:31:58] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.194.119.3:2342, load: 50%
[18:31:59] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.194.119.3:2342
[18:31:59] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.59.4.75:3172, load: 50%
[18:32:05] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 213.84.164.177:3380
[18:32:05] FastTrack: fst_session.c:128(fst_session_connect): connecting to 144.118.252.110:1951, load: 50%
[18:32:07] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.53.247.84:1214
[18:32:07] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.126.164.213:3364, load: 50%
[18:32:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 220.237.15.177:3703
[18:32:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.30.128.193:1303, load: 50%
[18:32:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 12.215.126.240:3386
[18:32:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.65.108.245:3359, load: 50%
[18:32:10] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:32:14] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.59.4.75:3172
[18:32:14] FastTrack: fst_session.c:128(fst_session_connect): connecting to 81.70.76.107:2766, load: 50%
[18:32:14] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:32:20] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 144.118.252.110:1951
[18:32:20] FastTrack: fst_session.c:128(fst_session_connect): connecting to 67.23.243.42:2218, load: 50%
[18:32:22] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.126.164.213:3364
[18:32:22] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.47.195.233:2109, load: 50%
[18:32:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 65.30.128.193:1303
[18:32:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 205.250.116.184:1684, load: 50%
[18:32:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.65.108.245:3359
[18:32:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.231.162.98:3460, load: 50%
[18:32:29] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 81.70.76.107:2766
[18:32:29] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.60.10.210:1629, load: 50%
[18:32:29] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.60.10.210:1629
[18:32:29] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.150.79.52:3748, load: 50%
[18:32:34] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:32:35] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 67.23.243.42:2218
[18:32:35] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.56.190.203:2415, load: 50%
[18:32:35] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[18:32:37] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.47.195.233:2109
[18:32:37] FastTrack: fst_session.c:128(fst_session_connect): connecting to 70.68.206.140:2051, load: 50%
[18:32:38] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[18:32:38] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.48.164.172:1215
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.60.190.223:1215
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.0.62.249:2145
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.184.241.41:1265
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.62.245.47:2145
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 132.177.56.63:1215
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 69.196.255.249:1215
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 155.47.148.103:1215
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 213.77.149.103:1889
[18:32:38] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 137.45.155.242:1215
[18:32:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 205.250.116.184:1684
[18:32:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.125.70.211:1883, load: 50%
[18:32:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.231.162.98:3460
[18:32:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 209.200.11.100:1443, load: 50%
[18:32:44] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.150.79.52:3748
[18:32:44] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.169.42.116:2710, load: 50%
[18:32:50] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.56.190.203:2415
[18:32:50] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.125.154.124:1214, load: 50%
[18:32:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 70.68.206.140:2051
[18:32:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.223.247.3:1638, load: 50%
[18:32:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.125.70.211:1883
[18:32:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.112.72.207:2793, load: 50%
[18:32:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 209.200.11.100:1443
[18:32:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.43.153.1:3091, load: 50%
[18:32:55] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[18:32:59] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.169.42.116:2710
[18:32:59] FastTrack: fst_session.c:128(fst_session_connect): connecting to 70.178.141.22:1066, load: 50%
[18:32:59] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings



//giftd.conf
[main]

# Boolean determining whether or not this file has been reviewed and is
# complete.  giFT will fail to start unless this is non-zero.  This is done
# so that we can make sure you, at the very least, read through this file.
# Default: 0
setup = 1

# Space separated list of hosts to allow connection to giFT's interface
# protocol (running default on port 1213).  This protocol is used for GUIs
# to communicate with giFT and could be considered a security risk to allow
# external connections.
# The following special keywords are supported:
#  ALL       - Synonym for 0.0.0.0/0
#  LOCAL     - Synonym for 127.0.0.0/8 192.168.0.0/16 172.0.0.0/11 10.0.0.0/8
# Bitwidth fields are optional.
# Default: LOCAL
hosts_allow = ALL

# Port on which to listen for user interface connections.  Unless you have a
# special need to talk to the client on a non-standard port, just accept the
# default.
# NOTE:
#  If you change this value, you will also need to modify the ui.conf
#  configuration for the machine which will be making outgoing connections
#  here.
client_port = 1213

# Determines whether or not to follow symbolic links.  If this value is set
# non-zero, symlinks will be traversed and a directory inode tracking system
# will be used to ensure that giFT does not descend the same directory
# twice.  If you do not have any symlinks or do not want them traversed, set
# this to 0 for a very minor efficiency gain.
# Windows users: this setting has no effect.
# Default: 1
follow_symlinks = 1

# Colon separated list of protocol plugins to load by default.  If dynamic
# library support is enabled, the plugin specified will be stat'd to check if
# it is a loadable path.  If that fails, the fallback method is to attempt to
# construct the fully qualified path based on the configured environment.
# NOTES:
#  Without dynamic library support, this plugin must have been compiled into
#  your giFT binary.  With, this plugin must exist in the installed
#  plugin directory.  giFT -V will output this path to you, if you are not
#  sure.
#  Protocol names are case sensitive, so use OpenFT, not Openft.
# For example, to use the OpenFT and Gnutella protocols use:
#  OpenFT:Gnutella
# Default: none
plugins = OpenFT:Gnutella:FastTrack

###############################################################################
# DOWNLOAD CONTROLS

[download]

# Directory to store transfers while they are being operated on.  Temporary
# state files are also kept here.  It is recommended, but not required, that
# the incoming and completed directories are on the same partition (drive).
# Windows users: please use the following path specification:
# incoming = /C/Program Files/giFT/incoming
# For example, to refer to C:\Program Files\giFT\incoming, use:
# incoming = /C/Program Files/giFT/incoming
# Default (*nix):    ~/.giFT/incoming
# Default (Windows): /C/Program Files/giFT/incoming
incoming = ~/.giFT/incoming

# Directory which will contain files after they have successfully finished
# downloading.
# Default (*nix):    ~/.giFT/completed
# Default (Windows): /C/Program Files/giFT/completed
completed = ~/Downloads/Shared

###############################################################################
# SHARE SUBMISSION AND UPLOAD CONTROL

[sharing]

# Maximum amount of uploads allowed from the same user at any given time.  It
# is recommended that you keep this at 1 in order to prevent users from
# unfairly queueing your connection.
# Default: 1
max_peruser_uploads = 1

# Determines whether or not to hide directories which contain a leading dot.
# These directories are commonly meant to be "hidden" and thus should not be
# submitted to the network.  Selecting 0 here will submit all directories.
# Default: 1
hide_dot_files = 1

# Colon separated list of fully qualified paths you wish to share.  These
# directories will be recursed at giFT's startup and the files contained
# within will be subjected to an MD5 hashing.  The results will be cached and
# will only be recalculated on a per share basis when the size or
# modification time in the cache and on disk disagree, or the file name is
# changed.
# Sanity notice:
#  Do NOT share source directories!  Remote nodes will refuse to index your
#  shares if you are attempting to submit more than 64000 files.
# Security notice:
#  Do not share directories which may contain sensitive information, such as
#  ~ ($HOME).  Also note that any directories shared here will be stripped of
#  all but the last path element when submitted to other nodes for indexing,
#  effectively "hiding" the directory prefix.
# Windows users: please use the following path specification:
#  /[drive]/dir1/dir2:/[drive]/dir3/dir4 ...
# For example, to refer to C:\Program Files\giFT\shares and D:\shares, use:
#  /C/Program Files/giFT/shares:/D/shares
# Default: none
root = 

# Maximum amount of simultaneous uploads allowed.  Setting this to -1 will
# cause giFT to not limit outgoing transfers.  0 effectively disables sharing.
# This may also be handled at run time via your GUI of choice.
# Default: -1
max_uploads = 0

# Controls when giFT periodically rescans your shared directories for any
# changes (new files, missing files, changed files, etc.) and communicates
# those changes to the underlying protocols.  This parameter specifies how
# often (in seconds) you want that to happen.
# For your reference
# 0        turns off periodic auto-resync
# 3600     one hour
# 86400    one day
# 604800   one week
# Default: 86400
auto_resync_interval = 86400

# Controls whether or not giFT should automatically share files that you have
# finished downloading.  This feature significantly improves the network's
# abundance of files and helps ease the load on those sharing popular files.
# It's a Good Thing (TM), please leave it on.
# Avoid setting your completed directories through sharing/root, as that
# setting will duplicate recursion of the completed directory and cause
# generally undesirable results.
# Default: 1
share_completed = 1

###############################################################################
# USER SPACE BANDWIDTH CONTROL

[bandwidth]

# Bandwidth throttling allows giFT to have some basic control over your
# bandwidth usage.  This code operates in user space, and as a result can not
# guarantee perfect accuracy.  If you wish to use this feature, please
# consider using a more reliable kernel space option first.  As always, google
# should be able to assist you there.
# The following configuration switches control the maximum number of bytes
# per second allowed for the given stream direction.  A setting of 0 will
# disable throttling for that direction.
# Default: 0
downstream = 0
upstream = 0

---

### Post by jillandjackk on 2011-07-05
Hello boss did you get the solution for this problem.I too got the same error.


If you have the solution please provide the fix for the problem

---

