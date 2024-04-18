import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class NomesAlunosUna {
    public static void main(String[] args) {
        String csvFile = "estudantes_una_2024.csv";
        String line = "";
        String csvSplitBy = ",";
        boolean firstLine = true;

        List<String> studentNames = new ArrayList<>();

        try (BufferedReader br = new BufferedReader(new FileReader(csvFile))) {
            while ((line = br.readLine()) != null) {
                if (firstLine) {

                    firstLine = false;
                    continue;
                }
                String[] studentData = line.split(csvSplitBy);
              
                String studentName = studentData[0].trim();
                studentNames.add(studentName);
            }

            Collections.sort(studentNames);

            for (int i = 0; i < studentNames.size(); i++) {
                String prefix = "Nome: ";
                System.out.println(prefix + studentNames.get(i));
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
