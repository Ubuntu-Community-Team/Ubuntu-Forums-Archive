---
title: "gscan2pdf to scan face-up"
date: 2008-04-20
forum: Desktop Environments
---

### Post by laluz on 2008-04-20
I have a Fujitsu ScanSnap 500S scanner that can scan multipage doublesided documents. To get the correct order of pages one has to put the document stack face down.  

 Has anybody managed to tell gscan2pdf to shuffle the resulting images so that it is possible to put the original face up? It seems more logical for me, and the original software coming with the scanner is able to do it. Should not be too complicated any ways?

Currently I have only found how to enable double sided scan and rotate pages by 180, so it is not necessary to put documents upside down.

---

### Post by JeffreyRatcliffe on 2008-04-20
> **laluz said:**
> I have a Fujitsu ScanSnap 500S scanner that can scan multipage doublesided documents. To get the correct order of pages one has to put the document stack face down.  

 Has anybody managed to tell gscan2pdf to shuffle the resulting images so that it is possible to put the original face up? It seems more logical for me, and the original software coming with the scanner is able to do it. Should not be too complicated any ways?

Currently I have only found how to enable double sided scan and rotate pages by 180, so it is not necessary to put documents upside down.

Please start gscan2pdf from the CLI, open the scan dialog, and post the output from the CLI so that I can see the options that SANE has for the scanner.

---

### Post by laluz on 2008-04-20
scanadf: rounded value of pageheight from 297 to 296.994
scanadf: rounded value of tl-x from 0 to 0
scanadf: rounded value of pagewidth from 210 to 210.01
scanadf: rounded value of resolution from 300 to 300
scanadf: rounded value of tl-y from 0 to 0
scanadf: rounded value of br-x from 210 to 210.01
scanadf: rounded value of br-y from 297 to 296.994


is this what you wanted to see? 
Thanks for a prompt reply!

---

### Post by laluz on 2008-04-20
```
gscan2pdf --debug
gscan2pdf 0.9.23
Using en_US.UTF-8 locale
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.12.0
$VAR1 = {
          'ocr panel' => '643',
          'frontend' => 'scanadf',
          'Paper' => {
                       'US Legal' => {
                                       'l' => '0',
                                       'y' => '356',
                                       'x' => '216',
                                       't' => '0'
                                     },
                       'US Letter' => {
                                        'l' => '0',
                                        'y' => '279',
                                        'x' => '216',
                                        't' => '0'
                                      },
                       'A4' => {
                                 'l' => '0',
                                 'y' => '297',
                                 'x' => '210',
                                 't' => '0'
                               }
                     },
          'mode' => 'Lineart',
          'unsharp radius' => '0',
          'window_maximize' => '',
          'ocr engine' => 'tesseract',
          'keywords' => '',
          'white-threshold' => '0.9',
          'pagewidth' => '210',
          'y' => '297',
          'layout' => 'single',
          'unsharp amount' => '1',
          'cwd' => '/xxxxxxxxxxxxxxxx',
          't' => '0',
          'OCR on scan' => '1',
          'image type' => 'pdf',
          'ocr language' => 'deu',
          'Paper size' => 'A4',
          'Page range' => 'all',
          'subject' => '',
          'window_height' => '999',
          'startup warning' => '',
          'rotate reverse' => '180',
          'pages to scan' => 'all',
          'resolution' => '300',
          'title' => 'Axxxxxxxxxxxxxxxxxxxx',
          'unpaper on scan' => '1',
          'source' => 'ADF Duplex',
          'rotate facing' => '180',
          'threshold' => '90',
          'author' => '',
          'x' => '210',
          'pageheight' => '297',
          'downsample dpi' => '150',
          'window_width' => '1280',
          'threshold tool' => '89',
          'window_x' => '10',
          'deskew-scan-direction' => 'left,right',
          'quality' => '75',
          'window_y' => '25',
          'date offset' => '0',
          'unsharp sigma' => '1',
          'thumb panel' => '160',
          'enable options' => '1',
          'version' => '0.9.23',
          'unsharp threshold' => '0.05',
          'device' => 'fujitsu:libusb:002:007',
          'l' => '0',
          'Page range default' => 'all',
          'downsample' => '',
          'restore window' => '1',
          'black-threshold' => '0.33',
          'TMPDIR' => '/tmp',
          'pdf compression' => 'jpg'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found tesseract
Found unpaper
Found libtiff
Using /tmp/B4ngxIU7zE for temporary files
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 31349
Waiting to reap process at /usr/bin/gscan2pdf line 3639.
Reaped PID -1
'0','fujitsu:libusb:002:007','FUJITSU ScanSnap S500'
scanadf --help --device-name='fujitsu:libusb:002:007' --mode='Lineart'
Forked PID 31359
Waiting to reap process at /usr/bin/gscan2pdf line 4586.
Reaped PID -1
Usage: scanadf [OPTION]...

Start image acquisition on a scanner device and write image data to
output files.

   [ -d | --device-name <device> ]   use a given scanner device.
   [ -h | --help ]                   display this help message and exit.
   [ -L | --list-devices ]           show available scanner devices.
   [ -v | --verbose ]                give even more status messages.
   [ -V | --version ]                print version information.
   [ -N | --no-overwrite ]           don't overwrite existing files.

   [ -o | --output-file <name> ]     name of file to write image data
                                     (%d replacement in output file name).
   [ -S | --scan-script <name> ]     name of script to run after every scan.
   [ --script-wait ]                 wait for scripts to finish before exit
   [ -s | --start-count <num> ]      page count of first scanned image.
   [ -e | --end-count <num> ]        last page number to scan.
   [ -r | --raw ]                    write raw image data to file.

Options specific to device `fujitsu:libusb:002:007':
  Scan Mode:
    --source ADF Front|ADF Back|ADF Duplex [ADF Front]
        Selects the scan source (such as a document-feeder).
    --mode Lineart|Halftone|Gray|Color [Lineart]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 50..600dpi (in steps of 1) [600]
        Sets the horizontal resolution of the scanned image.
    --y-resolution 50..600dpi (in steps of 1) [600]
        Sets the vertical resolution of the scanned image.
  Geometry:
    -l 0..215.872mm (in steps of 0.0211639) [0]
        Top-left x position of scan area.
    -t 0..279.364mm (in steps of 0.0211639) [0]
        Top-left y position of scan area.
    -x 0..215.872mm (in steps of 0.0211639) [215.872]
        Width of scan-area.
    -y 0..279.364mm (in steps of 0.0211639) [279.364]
        Height of scan-area.
    --pagewidth 0..221.121mm (in steps of 0.0211639) [215.872]
        Must be set properly to align scanning window
    --pageheight 0..863.489mm (in steps of 0.0211639) [279.364]
        Must be set properly to eject pages
  Enhancement:
    --threshold 0..255 (in steps of 1) [0]
        Select minimum-brightness to get a white point
    --rif[=(yes|no)] [no]
        Reverse image format
  Advanced:
    --dfdetect Default|None|Thickness|Length|Both [Default]
        Enable double feed sensors
    --dfdiff Default|10mm|15mm|20mm [Default]
        Difference in page length to trigger double feed sensor
    --dropoutcolor Default|Red|Green|Blue [Default]
        One-pass scanners use only one color during gray or binary scanning,
        useful for colored paper or ink
    --overscan Default|Off|On [Default]
        Collect a few mm of background on top side of scan, before paper
        enters ADF.
    --sleeptimer 0..60 (in steps of 1) [0]
        Time in minutes until the internal power supply switches to sleep mode
  Sensors and Buttons:

Type ``scanadf --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    fujitsu:libusb:002:007
$VAR1 = {
          'source' => {
                        'tip' => 'Selects the scan source (such as a document-feeder).',
                        'default' => 'ADF Front',
                        'values' => [
                                      'ADF Front',
                                      'ADF Back',
                                      'ADF Duplex'
                                    ]
                      },
          'rif' => {
                     'tip' => 'Reverse image format',
                     'default' => 'no',
                     'values' => [
                                   'yes',
                                   'no'
                                 ]
                   },
          'sleeptimer' => {
                            'tip' => 'Time in minutes until the internal power supply switches to sleep mode',
                            'step' => '1',
                            'min' => '0',
                            'max' => '60',
                            'default' => '0'
                          },
          'threshold' => {
                           'tip' => 'Select minimum-brightness to get a white point',
                           'step' => '1',
                           'min' => '0',
                           'max' => '255',
                           'default' => '0'
                         },
          'overscan' => {
                          'tip' => 'Collect a few mm of background on top side of scan, before paper enters ADF.',
                          'default' => 'Default',
                          'values' => [
                                        'Default',
                                        'Off',
                                        'On'
                                      ]
                        },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Lineart',
                      'values' => [
                                    'Lineart',
                                    'Halftone',
                                    'Gray',
                                    'Color'
                                  ]
                    },
          'dfdiff' => {
                        'tip' => 'Difference in page length to trigger double feed sensor',
                        'default' => 'Default',
                        'values' => [
                                      'Default',
                                      '10mm',
                                      '15mm',
                                      '20mm'
                                    ]
                      },
          'pageheight' => {
                            'tip' => 'Must be set properly to eject pages',
                            'step' => '0.0211639',
                            'min' => '0',
                            'max' => '863.489',
                            'default' => '279.364'
                          },
          'pagewidth' => {
                           'tip' => 'Must be set properly to align scanning window',
                           'step' => '0.0211639',
                           'min' => '0',
                           'max' => '221.121',
                           'default' => '215.872'
                         },
          'dfdetect' => {
                          'tip' => 'Enable double feed sensors',
                          'default' => 'Default',
                          'values' => [
                                        'Default',
                                        'None',
                                        'Thickness',
                                        'Length',
                                        'Both'
                                      ]
                        },
          'y-resolution' => {
                              'tip' => 'Sets the vertical resolution of the scanned image.',
                              'step' => '1',
                              'min' => '50',
                              'max' => '600',
                              'default' => '600'
                            },
          'dropoutcolor' => {
                              'tip' => 'One-pass scanners use only one color during gray or binary scanning, useful for colored paper or ink',
                              'default' => 'Default',
                              'values' => [
                                            'Default',
                                            'Red',
                                            'Green',
                                            'Blue'
                                          ]
                            },
          'resolution' => {
                            'tip' => 'Sets the horizontal resolution of the scanned image.',
                            'step' => '1',
                            'min' => '50',
                            'max' => '600',
                            'default' => '600'
                          }
        };
```

---

### Post by JeffreyRatcliffe on 2008-04-21
> **laluz said:**
> gscan2pdf --debug
gscan2pdf 0.9.23


Thanks, it was the --debug output that I meant.

There aren't any options there that look as though they would sort your problem out. On the other hand, presumably the original software was written explicity for your scanner.

Have you tried putting the paper in rotated 180? That way you don't need the rotate option.

---

### Post by laluz on 2008-04-21
> **JeffreyRatcliffe said:**
> 
There aren't any options there that look as though they would sort your problem out. On the other hand, presumably the original software was written explicity for your scanner.


I can imagine this happens in the software itself. What is needed is just a renumbering of scanned pages in the reverse order. Would it be complicated to add a checkbox for such a feature in the scan dialog? 
There are other scanners that have the same scanning order, so their owner could all profit from this.
Could you add the reverse numbering option?

> **JeffreyRatcliffe said:**
> 
Have you tried putting the paper in rotated 180? That way you don't need the rotate option.

I have enabled the rotation to 180 exactly to avoid putting the paper in rotated 180. So this is OK with me.

The main UI principle here is to put the document in the scanner as I would read it myself. That is first page up, upside up. Quite easy to remember. Computers should do the work :)

The use case is the following: I receive paper mail, bills and what not, scan all these documents and OCR them. Their content is being added to a full text search database. The windows software also makes thumbnails, so I can later visually sort the documents by their type into folders. Every document gets a date and some random number as their name. When I need a document I would just search for the keywords and view the results. Or I could go into folder and find a document by date or thumbnail view. Paper documents go into a shoebox and in the best case are never ever retrieved afterwards.

Usually it works like a charm, I do not have to spend to much time sorting the paper into physical folder, and can find all I need in seconds.

With gscan2pdf there are only few small features missing:
1. the subject of this thread
2. removal of empty pages if the documents are one-sided
3. possiblity to automatically save/name the resulting PDFs with date in their name, without navigating or typing in the file dialogs

I believe gscan2pdf could be extremely usefull for this use case, and there might be many who could make thier life easier doing their document management like this.

Thumbnails and full text search are already available through OS or google desktop, so this is already working.

---

### Post by JeffreyRatcliffe on 2008-04-22
> **laluz said:**
> What is needed is just a renumbering of scanned pages in the reverse order.

I can add a main menu item. There is already a Renumber item; a reverse numbering item would fit there.

> **laluz said:**
> Would it be complicated to add a checkbox for such a feature in the scan dialog? 

The checkbox is easy. The resulting behaviour is trickier ;-) The trouble I see is that there is no way of knowing in advance how many pages there are to be scanned. Therefore, the only reliable way of doing this from the scan dialog is to always insert each scan at page 1 and renumber the rest.

OK so far, but what do you do when there were pages already there?

Do you note how many pages were already there and insert after the last each time?

> **laluz said:**
> The use case is the following: I receive paper mail, bills and what not, scan all these documents and OCR them. Their content is being added to a full text search database. The windows software also makes thumbnails, so I can later visually sort the documents by their type into folders. Every document gets a date and some random number as their name. When I need a document I would just search for the keywords and view the results. Or I could go into folder and find a document by date or thumbnail view. Paper documents go into a shoebox and in the best case are never ever retrieved afterwards.

Usually it works like a charm, I do not have to spend to much time sorting the paper into physical folder, and can find all I need in seconds.

With gscan2pdf there are only few small features missing:
1. the subject of this thread
2. removal of empty pages if the documents are one-sided
3. possiblity to automatically save/name the resulting PDFs with date in their name, without navigating or typing in the file dialogs

I use gscan2pdf more or less in the same manner.

Removal of empty pages is not completely straightforward - especially as no page is completely empty, taking noise, etc. into account.

Adding the date from the PDF metatag to the filename wouldn't be hard.

---

### Post by laluz on 2008-04-30
> **JeffreyRatcliffe said:**
> 
The checkbox is easy. The resulting behaviour is trickier ;-) The trouble I see is that there is no way of knowing in advance how many pages there are to be scanned. Therefore, the only reliable way of doing this from the scan dialog is to always insert each scan at page 1 and renumber the rest.

OK so far, but what do you do when there were pages already there?

I see what you mean. To be honest with you, in this scenario the gscan2pdf is actually to be used in a batch mode. That is, once configured, I would not even need to see the application window. Ideally the app would listen to the scanner button and then process the document. 

I could imagine a checkbox, that makes gscan2pdf run in a daemon mode, sitting in a tray. It would then just let scanner send all pages, process them (including renumbering if needed) and save them. Then it would clean the working cue and wait for next batch from scanner.

The flexibility of selective work with the individual pages is lost, but it is actually not needed for these use case.


> **JeffreyRatcliffe said:**
> 
Removal of empty pages is not completely straightforward - especially as no page is completely empty, taking noise, etc. into account.

This might be an interesting task for whoever is in charge of the cleaning tool for the gscan2pdf toolchain. Would you consider challenging him on this?

---

### Post by JeffreyRatcliffe on 2008-04-30
You can already achieve the reverse numbering, it occurs to me - just select extended page numbering, set the start page to a number higher than the number of pages you are going to scan, the increment to -1, and you should be good to go.

---

### Post by laluz on 2008-04-30
After we had this short chat here I think I can recap my requirement as: to be able to scan to pdf with one push of a button any multipage double sided documents putting them face up top up into the duplex auto-feed scanner.

I think this is a worth goal, as this can help save time tremendously almost at the level of a lifestyle change.

---

