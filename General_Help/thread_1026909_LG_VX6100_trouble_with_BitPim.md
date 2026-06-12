---
title: "LG VX6100 trouble with BitPim"
date: 2008-12-31
forum: General Help
---

### Post by yonexFactory on 2008-12-31
I'm having trouble connecting my LG VX6100 with BitPim. It will not detect the phone even though it's definitely connected (when I plug it in, I get a dialogue about configuring it as a mobile broadband device). It says, "No phone detected/recognized," and if I set up the phone type and com port manually, it still will not work. I'm doing everything the same way I did with my previous phone, which worked like a charm, but no luck. Oh, and running BitPim as root doesn't work either.

If I just ignore the no detection message and try to get or send phone data, this is the error I get:
```
Traceback (most recent call last):
  File "src/gui.py", line 284, in run
  File "src/gui.py", line 159, in __call__
  File "src/gui.py", line 1884, in getdata
  File "src/gui.py", line 1878, in getfundamentals
  File "src/phones/com_lgvx4400.py", line 96, in getfundamentals
TypeError: sha1() argument 1 must be string or read-only buffer, not None

Variables by last 8 frames, innermost last

Frame run in src/gui.py at line 277
       resultcb =  <gui.Callback instance at 0xc9676cc>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon)>
           item =  (<gui.Request instance at 0x9cf82cc>, <gui.Callback instance at 0xc9676cc>)
           call =  <gui.Request instance at 0x9cf82cc>
             ex =  TypeError('sha1() argument 1 must be string or read-only buffer, not None',)
              e =  TypeError('sha1() argument 1 must be string or read-only buffer, not None',)
          first =  0

Frame __call__ in src/gui.py at line 159
           self =  <gui.Request instance at 0x9cf82cc>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getdata in src/gui.py at line 1884
           self =  <WorkerThread(BitPim helper, started daemon)>
            req =  <guiwidgets.GetPhoneDialog; proxy of <Swig Object of type 'wxDialog *' at 0xabb1
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame getfundamentals in src/gui.py at line 1878
           self =  <WorkerThread(BitPim helper, started daemon)>
        results =  Keys []
                   {}

Frame getfundamentals in src/phones/com_lgvx4400.py at line 96
           self =  <phones.com_lgvx6100.Phone object at 0xb080f0c>
        results =  Keys []
                   {}

BitPim Log:
15:46:40.961 USB Comm Watch started
15:47:02.235 coms:[{'available': True, 'description': 'USB modem (/dev/ttyACM0)', 'driver': 'ttyACM', 'device': (166, 0), 'class': 'modem', 'name': '/dev/ttyACM0'}, {'available': False, 'driver-required': True, 'protocol': 'Data / Generic', 'name': 'usb::005::002::1', 'VID': '0x1004', 'usb-vendor': 'LG Electroncs', 'description': 'USB Device - Vendor LG Electroncs, Product VX Series Phone (Direct USB connection), (Interface Modem Interface)', 'PID': '0x6000', 'usb-vendor#': 4100, 'usb-interface#': 1, 'usb-productstring': 'Qualcomm CDMA Technologies MSM', 'usb-product': 'VX Series Phone (Direct USB connection)', 'active': True, 'libusb': True, 'usb-product#': 24576, 'usb-interface': 'Modem Interface'}, {'available': True, 'usb-vendor': 'LG Electroncs', 'protocol': 'Vendor Specific Class / Vendor Specific Subclass', 'name': 'usb::005::002::2', 'VID': '0x1004', 'description': 'USB Device - Vendor LG Electroncs, Product VX Series Phone (Direct USB connection), (Interface Diagnostics Interface)', 'PID': '0x6000', 'usb-vendor#': 4100, 'usb-interface#': 2, 'usb-productstring': 'Qualcomm CDMA Technologies MSM', 'usb-product': 'VX Series Phone (Direct USB connection)', 'active': True, 'libusb': True, 'usb-product#': 24576, 'usb-interface': 'Diagnostics Interface'}, {'available': False, 'usb-vendor': 'Seagate RSS LLC', 'protocol': 'Mass Storage / SCSI / Bulk (Zip)', 'name': 'usb::001::003::0', 'VID': '0x0BC2', 'PID': '0x3000', 'usb-vendor#': 3010, 'usb-interface#': 0, 'active': True, 'libusb': True, 'usb-product#': 12288, 'description': 'USB Device - Vendor Seagate RSS LLC, Product #3000, (Interface #00)'}]
15:47:02.252 Available ports: ['/dev/ttyACM0', 'usb::005::002::2']
15:47:02.252 Available modem ports: ['/dev/ttyACM0']
15:47:02.343 Gathering data on port: /dev/ttyACM0
15:47:02.376 /dev/ttyACM0: Opening port /dev/ttyACM0, 115200 baud, timeout 1.000000, hardwareflow 0, softwareflow 0
15:47:02.376 /dev/ttyACM0: Open of comm port suceeded
15:47:02.377 Done on port: /dev/ttyACM0
15:47:02.377 Checking for model: E815
15:47:02.395 Likely ports:[]
15:47:02.396 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}}
15:47:02.396 Checking for model: E815m
15:47:02.396 Likely ports:[]
15:47:02.396 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}}
15:47:02.397 Checking for model: K1m
15:47:02.397 Likely ports:[]
15:47:02.397 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}}
15:47:02.402 Checking for model: LG-AX8600
15:47:02.524 Likely ports:['usb::005::002::2']
15:47:02.525 usb::005::002::2: Opening port usb::005::002::2, 115200 baud, timeout 1.000000, hardwareflow 0, softwareflow 0
15:47:02.526 usb::005::002::2: Open of comm port suceeded
15:47:02.526 LG-AX8600: Attempting to contact phone
15:47:04.535 usb::005::002::2: Timed out - flushing and trying again
15:47:06.544 usb::005::002::2: Timed out waiting for 7e, requested bytes -99999  - 0 bytes read
15:47:06.559 usb::005::002::2: Port speed 38400 not supported
15:47:06.572 usb::005::002::2: Port speed 115200 not supported
15:47:06.572 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.587 Checking for model: LG-C2000
15:47:06.649 Likely ports:[]
15:47:06.649 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.649 Checking for model: LG-G4015
15:47:06.649 Likely ports:[]
15:47:06.649 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.649 Checking for model: LG-LG6190
15:47:06.650 Likely ports:['usb::005::002::2']
15:47:06.650 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.650 Checking for model: LG-LG6200
15:47:06.717 Likely ports:['usb::005::002::2']
15:47:06.718 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.718 Checking for model: LG-LG8100
15:47:06.719 Likely ports:['usb::005::002::2']
15:47:06.719 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.720 Checking for model: LG-LX5450
15:47:06.720 Likely ports:['usb::005::002::2']
15:47:06.720 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.720 Checking for model: LG-LX5550
15:47:06.796 Likely ports:[]
15:47:06.797 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.797 Checking for model: LG-LX570 (Musiq)
15:47:06.799 Likely ports:['usb::005::002::2']
15:47:06.799 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.803 Checking for model: LG-PM225
15:47:06.821 Likely ports:['usb::005::002::2']
15:47:06.821 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.821 Checking for model: LG-PM325
15:47:06.821 Likely ports:['usb::005::002::2']
15:47:06.821 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.822 Checking for model: LG-TM520
15:47:06.822 Checking for model: LG-UX5000
15:47:06.822 Likely ports:['usb::005::002::2']
15:47:06.823 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:06.823 Checking for model: LG-VI125
15:47:07.108 Likely ports:['usb::005::002::2']
15:47:07.109 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.109 Checking for model: LG-VI5225
15:47:07.109 Likely ports:['usb::005::002::2']
15:47:07.109 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.109 Checking for model: LG-VX10
15:47:07.109 Checking for model: LG-VX10000 (Voyager)
15:47:07.109 Likely ports:['usb::005::002::2']
15:47:07.110 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.110 Checking for model: LG-VX3200
15:47:07.110 Likely ports:[]
15:47:07.110 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.110 Checking for model: LG-VX4400
15:47:07.111 Likely ports:['usb::005::002::2']
15:47:07.126 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.131 Checking for model: LG-VX4500
15:47:07.131 Likely ports:[]
15:47:07.131 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.131 Checking for model: LG-VX4600
15:47:07.132 Likely ports:['usb::005::002::2']
15:47:07.133 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.133 Checking for model: LG-VX4650
15:47:07.133 Likely ports:['usb::005::002::2']
15:47:07.133 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.133 Checking for model: LG-VX5200
15:47:07.134 Likely ports:['usb::005::002::2']
15:47:07.134 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.134 Checking for model: LG-VX5300
15:47:07.243 Likely ports:['usb::005::002::2']
15:47:07.244 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.244 Checking for model: LG-VX5400
15:47:07.244 Likely ports:['usb::005::002::2']
15:47:07.244 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.245 Checking for model: LG-VX6000
15:47:07.245 Likely ports:['usb::005::002::2']
15:47:07.245 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.246 Checking for model: LG-VX6100
15:47:07.252 Likely ports:['usb::005::002::2']
15:47:07.252 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.252 Checking for model: LG-VX7000
15:47:07.252 Likely ports:['usb::005::002::2']
15:47:07.253 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.253 Checking for model: LG-VX8000
15:47:07.255 Likely ports:['usb::005::002::2']
15:47:07.255 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.255 Checking for model: LG-VX8100
15:47:07.256 Likely ports:['usb::005::002::2']
15:47:07.256 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.256 Checking for model: LG-VX8300
15:47:07.256 Likely ports:['usb::005::002::2']
15:47:07.257 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.257 Checking for model: LG-VX8350
15:47:07.257 Likely ports:['usb::005::002::2']
15:47:07.257 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.259 Checking for model: LG-VX8500 (Chocolate)
15:47:07.259 Likely ports:['usb::005::002::2']
15:47:07.259 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.260 Checking for model: LG-VX8550 (Chocolate 2)
15:47:07.261 Likely ports:['usb::005::002::2']
15:47:07.261 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.261 Checking for model: LG-VX8560 (Chocolate 3)
15:47:07.261 Likely ports:['usb::005::002::2']
15:47:07.262 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.262 Checking for model: LG-VX8600
15:47:07.262 Likely ports:['usb::005::002::2']
15:47:07.263 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.263 Checking for model: LG-VX8610 (Decoy)
15:47:07.263 Likely ports:['usb::005::002::2']
15:47:07.263 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.263 Checking for model: LG-VX8700
15:47:07.263 Likely ports:['usb::005::002::2']
15:47:07.263 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.264 Checking for model: LG-VX8800 (Venus)
15:47:07.264 Likely ports:['usb::005::002::2']
15:47:07.264 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.264 Checking for model: LG-VX9100 (enV 2)
15:47:07.265 Likely ports:['usb::005::002::2']
15:47:07.274 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.274 Checking for model: LG-VX9400
15:47:07.274 Likely ports:['usb::005::002::2']
15:47:07.274 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.274 Checking for model: LG-VX9700 (Dare)
15:47:07.274 Likely ports:['usb::005::002::2']
15:47:07.274 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.274 Checking for model: LG-VX9800
15:47:07.274 Likely ports:['usb::005::002::2']
15:47:07.275 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.275 Checking for model: LG-VX9900 (enV)
15:47:07.275 Likely ports:['usb::005::002::2']
15:47:07.275 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.275 Checking for model: MM-5600
15:47:07.527 Checking for model: MM-7400
15:47:07.527 Checking for model: MM-7500
15:47:07.589 Likely ports:[]
15:47:07.589 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.589 Checking for model: MM-8300
15:47:07.589 Checking for model: Other CDMA phone
15:47:07.589 Checking for model: PM-8200
15:47:07.589 Checking for model: RL-4920
15:47:07.590 Checking for model: RL-4930
15:47:07.590 Checking for model: SCH-A310
15:47:07.658 Likely ports:[]
15:47:07.658 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.659 Checking for model: SCH-A650
15:47:07.659 Likely ports:[]
15:47:07.659 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.660 Checking for model: SCH-A670
15:47:07.660 Likely ports:[]
15:47:07.661 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.661 Checking for model: SCH-A870
15:47:07.836 Likely ports:[]
15:47:07.837 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.837 Checking for model: SCH-A930
15:47:07.838 Likely ports:[]
15:47:07.838 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.838 Checking for model: SCH-A950
15:47:07.846 Likely ports:[]
15:47:07.846 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.847 Checking for model: SCH-U470
15:47:07.847 Likely ports:[]
15:47:07.847 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.847 Checking for model: SCH-U740
15:47:07.848 Likely ports:[]
15:47:07.848 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.848 Checking for model: SCP-200
15:47:07.848 Checking for model: SCP-2400
15:47:07.848 Likely ports:[]
15:47:07.848 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.848 Checking for model: SCP-3100
15:47:07.848 Likely ports:[]
15:47:07.848 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.848 Checking for model: SCP-3200
15:47:07.848 Likely ports:[]
15:47:07.849 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.849 Checking for model: SCP-4900
15:47:07.849 Checking for model: SCP-5300
15:47:07.849 Checking for model: SCP-5400
15:47:07.849 Checking for model: SCP-5500
15:47:07.849 Checking for model: SCP-6600 (Katana)
15:47:07.849 Likely ports:[]
15:47:07.849 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.849 Checking for model: SCP-6650 (Katana-II)
15:47:07.849 Likely ports:[]
15:47:07.850 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.850 Checking for model: SCP-7050
15:47:07.850 Likely ports:[]
15:47:07.850 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:07.850 Checking for model: SCP-7200
15:47:07.850 Checking for model: SCP-7300
15:47:07.850 Checking for model: SCP-8100
15:47:07.850 Checking for model: SCP-8100 (Bell)
15:47:08.011 Checking for model: SCP-8400
15:47:08.012 Likely ports:[]
15:47:08.012 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.013 Checking for model: SK6100
15:47:08.013 Checking for model: SPH-A460
15:47:08.014 Checking for model: SPH-A620 (VGA1000)
15:47:08.014 Checking for model: SPH-A660 (VI660)
15:47:08.014 Checking for model: SPH-A680
15:47:08.015 Checking for model: SPH-A740
15:47:08.015 Checking for model: SPH-A840
15:47:08.015 Checking for model: SPH-A840 (Telus)
15:47:08.016 Checking for model: SPH-A900
15:47:08.016 Checking for model: SPH-M300MEDIA
15:47:08.016 Likely ports:[]
15:47:08.017 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.017 Checking for model: SPH-M300PIM
15:47:08.017 Checking for model: SPH-N200
15:47:08.017 Checking for model: SPH-N400
15:47:08.017 Checking for model: V325
15:47:08.017 Likely ports:[]
15:47:08.018 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.018 Checking for model: V325M
15:47:08.018 Likely ports:[]
15:47:08.018 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.018 Checking for model: V3c
15:47:08.346 Likely ports:[]
15:47:08.346 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.347 Checking for model: V3cm
15:47:08.347 Likely ports:[]
15:47:08.347 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.347 Checking for model: V3m
15:47:08.348 Likely ports:[]
15:47:08.348 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.348 Checking for model: V3mM
15:47:08.348 Likely ports:[]
15:47:08.348 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.348 Checking for model: V710
15:47:08.348 Likely ports:[]
15:47:08.348 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.348 Checking for model: V710m
15:47:08.349 Likely ports:[]
15:47:08.349 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:08.349 Checking for model: VI-2300
15:47:08.349 Checking for model: VM4050
15:47:08.349 Likely ports:[]
15:47:08.349 Detect Phone result: {'/dev/ttyACM0': {'mode_modem': True, 'mode_brew': False, 'firmwareresponse': None, 'esn': '23E972E1', 'model': 'VX6100 108', 'firmware_version': 'S/W VER: DP3.3 PATCH  T61VZV01 ', 'manufacturer': 'LG Electronics Inc.'}, 'usb::005::002::2': {'mode_modem': None, 'mode_brew': False, 'firmwareresponse': None, 'esn': None, 'model': None, 'firmware_version': None, 'manufacturer': None}}
15:47:18.323 usb::004::003::2: Opening port usb::004::003::2, 115200 baud, timeout 3.000000, hardwareflow 0, softwareflow 0
15:47:18.323 usb::004::003::2: Failed to find usb::004::003::2.  You may need to rescan.
15:47:18.323 Error: Failed to open communications - <>
<>: Failed to find usb device usb::004::003::2
15:47:53.708 usb::005::002::2: Opening port usb::005::002::2, 115200 baud, timeout 3.000000, hardwareflow 0, softwareflow 0
15:47:53.709 usb::005::002::2: Open of comm port suceeded
15:47:53.709 LG-VX6100: Attempting to contact phone
15:47:53.709 LG-VX6100: Retrieving fundamental phone information
15:47:53.709 LG-VX6100: Phone serial number
15:47:53.709 LG-VX6100: Getting file contents 'nvm/$SYS.ESN'
15:47:59.702 usb::005::002::2: Timed out - flushing and trying again
15:48:05.711 usb::005::002::2: Timed out waiting for 7e, requested bytes -99999  - 0 bytes read
15:48:11.732 usb::005::002::2: Timed out - flushing and trying again
15:48:17.741 usb::005::002::2: Timed out waiting for 7e, requested bytes -99999  - 0 bytes read
15:48:17.743 usb::005::002::2: Port speed 38400 not supported
15:48:17.744 usb::005::002::2: Port speed 115200 not supported
15:48:20.753 usb::005::002::2: Read Exception: could not set config 1: Device or resource busy
15:48:20.783 LG-VX6100: No response to AT+GMM
15:48:23.791 usb::005::002::2: Read Exception: could not set config 1: Device or resource busy
15:48:23.822 LG-VX6100: No response to setting QCDMG mode
15:48:23.825 usb::005::002::2: Port speed 115200 not supported
15:48:23.825 usb::005::002::2: Port speed 19200 not supported
15:48:23.825 usb::005::002::2: Port speed 230400 not supported
15:48:29.835 usb::005::002::2: Timed out - flushing and trying again
15:48:35.844 usb::005::002::2: Timed out waiting for 7e, requested bytes -99999  - 0 bytes read
15:48:35.845 usb::005::002::2: Port speed 38400 not supported
15:48:35.846 usb::005::002::2: Port speed 115200 not supported
15:48:35.859 Exception: BitPim version: 1.0.6-official
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "src/gui.py", line 284, in run
  File "src/gui.py", line 159, in __call__
  File "src/gui.py", line 1884, in getdata
  File "src/gui.py", line 1878, in getfundamentals
  File "src/phones/com_lgvx4400.py", line 96, in getfundamentals
TypeError: sha1() argument 1 must be string or read-only buffer, not None

Variables by last 8 frames, innermost last

Frame run in src/gui.py at line 277
       resultcb =  <gui.Callback instance at 0xc9676cc>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon)>
           item =  (<gui.Request instance at 0x9cf82cc>, <gui.Callback instance at 0xc9676cc>)
           call =  <gui.Request instance at 0x9cf82cc>
             ex =  TypeError('sha1() argument 1 must be string or read-only buffer, not None',)
              e =  TypeError('sha1() argument 1 must be string or read-only buffer, not None',)
          first =  0

Frame __call__ in src/gui.py at line 159
           self =  <gui.Request instance at 0x9cf82cc>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getdata in src/gui.py at line 1884
           self =  <WorkerThread(BitPim helper, started daemon)>
            req =  <guiwidgets.GetPhoneDialog; proxy of <Swig Object of type 'wxDialog *' at 0xabb1
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame getfundamentals in src/gui.py at line 1878
           self =  <WorkerThread(BitPim helper, started daemon)>
        results =  Keys []
                   {}

Frame getfundamentals in src/phones/com_lgvx4400.py at line 96
           self =  <phones.com_lgvx6100.Phone object at 0xb080f0c>
        results =  Keys []
                   {}
```

Any help would be appreciated.

Thanks,
Nick

---

### Post by dgatwood on 2009-10-07
I know this won't help you, but I've experienced the exact same problem with two different LG phones in Mac OS X.  So whatever is going on, the problem is either a cross-platform bug in libusb or, more likely, a cross-platform bug in bitpim.  It's clearly detecting the device (at the OS level), and even talking to the device up to a point.

More importantly, since your failure and my failure are occurring in exactly the same spot in the communication with exactly the same error (all the way down to the negative byte count), that pretty much rules out any possibility that my cable is poorly shielded and is dropping data or something.  It's good to have that info when I file a problem report about it tomorrow.

---

### Post by projectgreen on 2009-11-15
I had a similar issue, if not the same.  Ubuntu 8.04 running bitpim-1.0.2

I found that the vx6100 gets confused easily.  Here's what I did:

First, I added this fix to prototypes.py on line 88:
 class BaseProtogenClass(object):
     """All types are derived from this"""
+    def __init__(self, *args, **kwords):
+	return
+
     def packetsize(self):
         "Returns size in bytes that we occupy"
         # This is implemented by writing to a buffer and seeing how big the result is.
Not sure if that was necessary or not, but the fix came per
[https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/395830](https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/395830)

Then:
2. Unplug the phone from the USB cable; kill bitpim
3. Restart the phone.
4. Under Settings/Data in the phone set Data/Fax to "Data in Always" and set PC  Connection to RS-232C.  (If the phone is confused, this will stay on "USB" and won't change.)
5. Plug the phone into the USB cable.
6. Go back and do step 4 again!  The phone changes settings when you plug the cable in.
7. Start bitpim as root. Under settings select the 2nd USB port (usb::005::004::2) for the phone (Interface Diagnostics Interface), not ttyACM0.
8. Hit "Get Phone Data" in bitpim and you should be good to go.  

I've tried other settings, like USB mode on the phone, and communicating through ttyACM0 in bitpim, but none of those seem to work.

---

### Post by peril on 2009-12-28
This worked aok with my vx9100 - make sure to indent things right - think that python is whitespace delimited ... I wonder why this just isn't in the default of bitpim.

```
class BaseProtogenClass(object):
    """All types are derived from this"""
    def __init__(self, *args, **kwords):
        return
```the return is indented (and the def __init__) is as well - but the other methods underneath provide a good guestimate for the amount of indent.

(DAMN this editor eating up my whitespace.)

---

### Post by ethanay on 2010-11-21
> **projectgreen said:**
> I had a similar issue, if not the same.  Ubuntu 8.04 running bitpim-1.0.2

I found that the vx6100 gets confused easily.  Here's what I did:

First, I added this fix to prototypes.py on line 88:
 class BaseProtogenClass(object):
     """All types are derived from this"""
+    def __init__(self, *args, **kwords):
+	return
+
     def packetsize(self):
         "Returns size in bytes that we occupy"
         # This is implemented by writing to a buffer and seeing how big the result is.
Not sure if that was necessary or not, but the fix came per
[https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/395830](https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/395830)

This was not necessary for me.  The rest of your solution allowed me to connect successfully to my phone:

> 
Then:
2. Unplug the phone from the USB cable; kill bitpim
3. Restart the phone.
4. Under Settings/Data in the phone set Data/Fax to "Data in Always" and set PC  Connection to RS-232C.  (If the phone is confused, this will stay on "USB" and won't change.)
5. Plug the phone into the USB cable.
6. Go back and do step 4 again!  The phone changes settings when you plug the cable in.
7. Start bitpim as root. Under settings select the 2nd USB port (usb::005::004::2) for the phone (Interface Diagnostics Interface), not ttyACM0.
8. Hit "Get Phone Data" in bitpim and you should be good to go.  

I've tried other settings, like USB mode on the phone, and communicating through ttyACM0 in bitpim, but none of those seem to work.

THANK YOU!!!:guitar:

---

