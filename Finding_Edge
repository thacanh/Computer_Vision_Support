import cv2

def nothing(x):
    pass

def preProcessing(img_path):
    img = cv2.imread(img_path, cv2.IMREAD_GRAYSCALE)

    kernel_size = cv2.getTrackbarPos("Kernel Size", "Settings")
    kernel_size = kernel_size if kernel_size % 2 == 1 else kernel_size + 1
    imgPre = cv2.GaussianBlur(img, (kernel_size, kernel_size), 0)

    thresh1 = cv2.getTrackbarPos("Thresh1", "Settings")
    thresh2 = cv2.getTrackbarPos("Thresh2", "Settings")
    apply_binary = cv2.getTrackbarPos("Binary", "Settings")
    if apply_binary:
        _, imgPre = cv2.threshold(imgPre, 127, 255, cv2.THRESH_BINARY)
    imgPre = cv2.Canny(imgPre, thresh1, thresh2)

    return imgPre

cv2.namedWindow("Settings")
cv2.createTrackbar("Thresh1", "Settings", 0, 255, nothing)
cv2.createTrackbar("Thresh2", "Settings", 0, 255, nothing)
cv2.createTrackbar("Kernel Size", "Settings", 3, 21, nothing)  # Giá trị mặc định là 3
cv2.createTrackbar("Binary", "Settings", 0, 1, nothing)  # Tắt/Bật nhị phân hóa

while True:
    processed_img = preProcessing('01.jpg')
    cv2.imshow("Processed Image", processed_img)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cv2.destroyAllWindows()
