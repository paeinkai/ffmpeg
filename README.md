# ffmpeg

# video/audio out of sync
# audio filter resample async --> maximum 1 sample per second. first_pts starting from 0 second?
ffmpeg -i <source-file> -f mpegts -c:v copy -af aresample=async=1:first_pts=0 -

# CFR & CBR
# from ffmpeg https://trac.ffmpeg.org/wiki/Encode/H.264
ffmpeg -i input.mp4 -c:v libx264 -x264-params "nal-hrd=cbr" -b:v 1M -minrate 1M -maxrate 1M -bufsize 2M output.ts

