Adaptive Emoji
========================

In this activity, you will learn to create a filter which will adapt to the users facial expression.

<img src= "https://media.slid.es/uploads/1525749/images/10515184/72pcp.gif" width = "480" height = "320">


Follow the given steps to complete this activity:

1. Create a filter list .

* Open the main.py file.

* Create list to hold face images.

    `faceImages = []`

    `path = "Images/"`

    `pathList = os.listdir(path)`

    `pathList.sort()`

* Use for loop to loop through the `pathList`.

    `for x, pathImg in enumerate(pathList):`

* Read the image and append it in the `faceImages` list.

    `img = (cv2.imread(path+"/"+pathImg, cv2.IMREAD_UNCHANGED))`

    `img = cv2.resize(img, (100, 100))`

    `faceImages.append(img)`

* Creating object to detect hand and face.

    `detector = HandDetector(detectionCon=0.8)`

    `faceDetector = FaceMeshDetector(maxFaces=2)`

2. ### Show the emoji

* Create a function `showObjectOnface()` with paramters `backImg, frontImg, xLoc, yLoc, dist, rf, rx, ry` to place objects on the face.

    `def showObjectOnface(backImg, frontImg, xLoc, yLoc, dist, rf, rx, ry):`

* Set `resizefactor` to `dist/rf`.

        `resizefactor = dist/rf`

* Resize the front image using `resizefactor` and store it in `frontImg` variable.

        `frontImg = cv2.resize(frontImg, (0, 0), fx=resizefactor, fy=resizefactor)`

* Overlay the front image on the back image.

        `backImg = cvzone.overlayPNG(backImg, frontImg, [int(
        xLoc - (resizefactor*rx)), int(yLoc - (resizefactor * ry))])`

    `return backImg`

* Calculate the `lipOpenDistance` using `math.dist()` to calculate distance between `13 and 14` point .

    `lipOpenDistance = math.dist(face[13], face[14])`

* Calculate the `lipEndDistance` using `math.dist()` to calculate distance between `76 and 306` point.

    lipEndDistance = math.dist(face[76], face[306])
    
* Save and run the code to check the output.






