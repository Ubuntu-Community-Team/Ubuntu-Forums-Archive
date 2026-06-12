---
title: "getPortIdentifiers returns no ports"
date: 2010-07-03
forum: Desktop Environments
---

### Post by ubundhara on 2010-07-03
Hi everyone.. i am using Ubuntu 9.10 i686..32-bit and jdk version java-6-sun-1.6.0.16. i have installed the rxtx jar n the required file in ext and lib folders resp of jdk. The rxtx version i used is rxtx-2.1-7-bins-r2. The issue with my application is i m not getting any values in CommPortIdentifier.getPortIdentifiers() method & not getting any error also. i even explicitly added System.setProperty(“gnu.io.rxtx.SerialPorts”, “/dev/ttyACM0&#8243;); But yet no succcess !! I m tired of tryin everythin.. Can anyone point out the mistake.. Am i using a wrong version of rxtx or so.. Any help will be appriciated a lot.. TIA

---

### Post by kalohr on 2010-07-05
hello, I am also trying to control a device through parallel port
communication

from what I can tell the problem lies in Ubuntu configuration...

I am using Ubutu 8.04 LTS, kernel version 2.6.24-26

I have enabled the parport_pc and ppdev kernel modules with modprob and disabled the lp module, after reading various posts

have also changed the permissions to /dev/parport0 to 666

still, I get a non-null portIdentifier

is there a known parport configuration that works with rxtx?

or any ideas?

thanks all,

Kalohr

this is my code:

   public static void main(String[] args) {
               try{
                       CoinParallelPortManager coinMng = new
CoinParallelPortManager();

                       Enumeration portList =
CommPortIdentifier.getPortIdentifiers();

                       while (portList.hasMoreElements()) {
                               portIdTmp = (CommPortIdentifier)
portList.nextElement();
                               System.out.println("Found port:
"+portId.getName());
                               if (portIdTmp.getPortType() ==
CommPortIdentifier.PORT_PARALLEL) {
                                       System.out.println("Found
port: "+portIdTmp.getName());
                                       portId=portIdTmp;
                                       if (portId.getName().equals(portName)) {

System.out.println("Found port: ");
                                       }
                               }
                       }

                       parallelPort = (ParallelPort)(portId.open("test", 50));
                       parallelPort.addEventListener(coinMng);

                       InputStream inputStream = parallelPort.getInputStream();
                       while(true){
                               int str = (int)inputStream.read();
                               logger.info("READ "+str);
                       }
               }catch(Exception e){
                       logger.info(e.toString());
                       e.printStackTrace();
               }
       }

---

### Post by kalohr on 2010-07-09
I think that I have resolved my problem

the shared object libraries that I've downloaded from rxtx.org were not suitable for my system. For instance, entering ldd librxtxSerial.so returns that the library is invalid

I downloaded the source built and installed it and it worked for me

it is easy to to do it: sh ./configure; make; make install

alternatively, there are binaries for various systems distributed under the Tomboy rxtx distro, if I am not mistaken... 

kalohr

---

