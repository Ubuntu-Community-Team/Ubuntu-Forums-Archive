---
title: "[gscan2pdf-help]: scan starts but no document"
date: 2018-02-21
forum: Desktop Environments
---

### Post by mahjsa on 2018-02-21
After looking for the "error during device i/o" I get when I start a scan with Pixma MP560 I ran gscan2pdf with debug option. Following is the excerpt from the debut output I got after starting a scan. At first the scan seems to start OK, but after scanning I get the device i/o error and no document.
```
iting time in seconds for a new document inserted into the automatic document feeder.',
                                'index' => 25,
                                'name' => 'adf-wait',
                                'max_values' => 1,
                                'title' => 'ADF Waiting Time'
                              }
                            ],
                 'hash' => {
                             'br-x' => $VAR1->{'array'}[13],
                             'button-1' => $VAR1->{'array'}[17],
                             'source' => $VAR1->{'array'}[4],
                             'threshold' => $VAR1->{'array'}[23],
                             'tl-x' => $VAR1->{'array'}[11],
                             'scan-resolution' => $VAR1->{'array'}[21],
                             'adf-wait' => $VAR1->{'array'}[25],
                             'gamma' => $VAR1->{'array'}[9],
                             'threshold-curve' => $VAR1->{'array'}[24],
                             'target' => $VAR1->{'array'}[20],
                             'tl-y' => $VAR1->{'array'}[12],
                             'gamma-table' => $VAR1->{'array'}[8],
                             'button-update' => $VAR1->{'array'}[16],
                             'button-controlled' => $VAR1->{'array'}[5],
                             'custom-gamma' => $VAR1->{'array'}[7],
                             'resolution' => $VAR1->{'array'}[2],
                             'br-y' => $VAR1->{'array'}[14],
                             'original' => $VAR1->{'array'}[19],
                             'mode' => $VAR1->{'array'}[3],
                             'button-2' => $VAR1->{'array'}[18]
                           },
                 'source' => $VAR1->{'array'}[4]
               }, 'Gscan2pdf::Scanner::Options' );


DEBUG - Options do not support paper size 'US Legal'.
DEBUG - Options support paper size 'US Letter'.
DEBUG - Options support paper size 'A4'.
DEBUG - signal 'started-process' emitted with message: Setting option resolution
DEBUG - signal 'finished-process' emitted with data: set_option resolution to 150
INFO - rotate facing 0
INFO - rotate reverse 0
INFO - unpaper 
INFO - UDT 
INFO - Current UDT gimp %i
INFO - OCR 1
INFO - threshold-before-ocr 
Running sane_start for SANE_Handle 0x7ffac40415c0
Getting parameters for SANE_Handle 0x7ffac40415c0
INFO - gscan2pdf: scanning image of size 1276x1754 pixels at 24 bits/pixel
INFO - gscan2pdf: acquiring RGB frame
INFO - Scanning 1 pages from 1 with step 1
DEBUG - signal 'started-process' emitted with message: Scanning page 1 of 1
[bjnp] bjnp_recv_header: ERROR - could not read response header (select timed out after 1000 ms)!
[bjnp] bjnp_recv_header: ERROR - could not read response header (select timed out after 1000 ms)!
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 32, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 244, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
INFO - gscan2pdf: sane_read: Error during device I/O
INFO - gscan2pdf: min/max graylevel value = 255/0
INFO - Scanned page /tmp/gscan2pdf-NVKL/Tu2zR9pMyO.pnm. (scanner status = 9)
INFO - signal 'process-error' emitted with data: scan_pages Error during device I/O

```
So, where to go from here?

---

