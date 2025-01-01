#!/bin/sh

# Trap Ctrl+C (SIGINT) and do nothing
trap '' SIGINT

if [ ! -f /tmp/network-up ]; then
    /usr/bin/networking.sh
    touch /tmp/network-up
fi

setsid /usr/local/bin/valkey-server >> /tmp/valkey.log 2>&1 &
while ! echo | nc 127.0.0.1 6379; do sleep 0.1; done
clear
while true; do
    /usr/local/bin/valkey-cli
done
