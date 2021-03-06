Development of an adapter board design for [Kosagi Novena](http://kosagi.com/w/index.php?title=Novena_Main_Page) LVDS interface to connect to the "iPad 3" QXGA 2048x1536 eDP LCD panel (aka LG LP097QX1-SPC1 and related models). Possibly also a touch screen interface to suit that display...

* [Schematic PDF here](https://github.com/projectgus/novepad/raw/master/novepad-schematic.pdf)
* [Kosagi forum thread here](http://www.kosagi.com/forums/viewtopic.php?id=58).

**INITIAL PROTOTYPE STAGE, NOT A THING YET**

Very closely modelled on Bunnie's existing Novena eDP adapter, with additions. LVDS connection cable from Novena should be the same on both boards.

Designed using KiCad (2014-07-25, any recent version should be OK to open the files). [Gerbers are available from the releases page](https://github.com/projectgus/novepad/releases/).

# Additions to the Novena eDP design

* Backlight driver (2x TI [TPS61181](http://www.ti.com/product/tps61181))
* Touch screen controller Focaltech [FT5816LPC](http://www.focaltech-systems.com/En/solutions.aspx?CateID=54) with i2c and USB interfaces. There's a strong chance this will never work (lack of public documentation on controller or digitizer).
* 4 eDP lanes out of IT6251 eDP converter instead of the 2 used on Novena eDP board.

# Notes

* Has a lot of numbered test points and 0R resistors due to undocumented or unknown factors.
* Has cut trace jumpers for some key power connections, can be cut to measure power consumption.

# Board Stackup

4 layer board, 1oz copper (35um). Desired stackup is:

* Front copper
* 0.2mm prepreg
* GND (Inner1)
* 1.2mm prepreg
* VCC (Inner2)
* 0.2mm prepreg
* Back

(This matches standard 4 layer stackup for my usual prototype PCB supplier, [Hackvana](http://hackvana.com)).)

The 100 ohm differential microstrip traces (LVDS, eDP) are routed as 0.2mm trace / 0.15mm spacing (~8/6 imperial), at least where possible. This yields estimates in the range of 99.5-102ohm differential impedance depending on who you ask (assuming Er 4.4, calculated using [TNT Field Solver](http://mmtl.sourceforge.net/) and [Jean Nicolle's impedance calculator](http://www.fedevel.com/welldoneblog/2011/08/pcb-impedance-calculator-single-ended-differential-pair/).


# Resources

## Novena designs

Yay OSHW!

* http://kosagi.com/w/index.php?title=Novena_PVT_Design_Source

## iPad display/connectors

* http://emerythacks.blogspot.com.au/2013/04/connecting-ipad-retina-lcd-to-pc.html
* http://mikesmods.com/mm-wp/?s=ipad+3

## Photos of IT6251

You know a chip is going to be fun when **photos** of PCBs that use it become a useful resource to complement the datasheet.

* [overclock.net post with high-res photo of top of board](http://www.overclock.net/t/1225919/yamakasi-catleap-monitor-club/2110#post_16887300)
* [overclock.net lower-res photos incl back of board (no components)](http://www.overclock.net/t/1304102/catleap-q270-replacement-board#post_18163044)

