# kamtar
<pre>
Network simulation wrapper for tc | Network as in real life to help making offline apps

usage: ./kamtar [2g|3g|country|mountain|ride|test] [test]
-----------------------------------------------------------------
[2g]       Simulate bad 2g
            [~5-15 Kbps, high pîng, packet loss]
[3g]       Simulate bad 3g
            [~0.5 Mbps, 200/300ms pîng, some packet loss]
[country]   Simulate 2g/3g in flat countryside areas
            [~0.3 Mbps, 600/800ms, packet loss, breakings]
[moutain]  Simulate 2g/3g in mountains area
            [0->0.5 Mbps, >1500ms ping, dns failures]
[ride]     Simulation while moving fast
            [~0/4 Mbps, 100/5000ms pîng, dns failures]
[test]     Launch speedtest tools
</pre>

### WHY?

Web workers in browsers can detect and switch scripts to keep the page running while offline.

While debugers in browsers can throttle connexions, they can't switch off the network.

This is a helper script intented to help to write offline switching apps.

### HOW?

This is a shell script written in php.

It send commands to <b>tc</b> linux to slow down the network with high ping time that change in intervals.

The mountain and ride mode will furthermore cut down the main network card, then switch it back, in addition of high pings and packet losses.

There is no dependencies as it use tc linux system tool, but <b>speedtest-cli</b> for the test part.
Ping packets are sent to speedtest.net.

    sudo apt install speedtest-cli
    
### HOW TO DISABLE?

Just start the script without argument.

### Still, trouble, wtf?

sudo ifconfig CARDNAME up 
sudo tc qdisc del dev CARDNAME root netem


