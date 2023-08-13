# Download Text to Speech Sample
   1. Navigate to [https://cloud.google.com/text-to-speech#section-2](https://cloud.google.com/text-to-speech#section-2)
   2. Strike **F12** to open developer tools.
   3. Find and click on the **Network** tab within developer tools.
   4. Change **Voice name** to ```en-US-Neural2-C```.
   5. Increase **Pitch** to some value between 2 and 3.
   6. Click **SPEAK IT**, prove you're not a robot, and let the audio play for a moment.
   7. Pause the audio playback.
   8. Find your developer tools window with the network tab selected.
   9. In the **Filter** field, type ```cxl-services.appspot.com```
   10. This should filter all the network requests out except for one.
   11. Click on the single result and then find the **Response** tab.
   12. Select the entire value next to "audioContent" (including the quotes). It is a very long string of seemingly random letters and numbers.
   13. In the developer tools, find the **Console** tab and type ```var b = ```, then paste the value that you copied in the previous step, and then stike **Enter**. (ignore any errors relating to the console history)
   14. Copy and paste the following javascript into the **Console** tab and then strike **Enter**.
```js
function downloadTtsAudio(audiodata, filename){
    var a = document.createElement('a');
    a.setAttribute('href', "data:audio/wav;base64," + audiodata);
    a.setAttribute('download',filename);
    a.style.display = 'none';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
}
downloadTtsAudio(b,"speech_sample.wav");
```
   15. Check your **Downloads** folder.
